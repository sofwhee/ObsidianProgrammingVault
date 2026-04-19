#Rails #cloud

Facilitates uplading files to cloud storage.

  Amazon S3
  Google Cloud Storage
  Microsoft Azure Storage

The file gets attached to Active Record objects.

Local disk-based service for development.
Mirror files to services for backups/migrations.

--- Dependencies ---

libvips OR ImageMagick (image analysis/transformations)
ffmpeg (video previews)
ffprobe (video/audio analysis)
poppler OR muPDF (pdf previews)


(Compared to libvips, 
  ImageMagick is better known and more widely available. 
  However, libvips can be up to 
  10x faster and consume 1/10 the memory. 
  For JPEG files, this can be further improved by 
  replacing libjpeg-dev with libjpeg-turbo-dev, 
  which is 2-7x faster.)

--- Setup ---

bin/rails active_storage:install
bin/rails db:migrate

-- Declare Active Storage services (config/storage.yml)
  For each service your application uses, 
  provide a name and the requisite configuration. 
  The example below declares three services 
  named local, test

#
local:
  service: Disk
  root: <%= Rails.root.join("storage") %>

test:
  service: Disk
  root: <%= Rails.root.join("tmp/storage") %>
#

#
amazon:
  service: S3
  access_key_id: ""
  secret_access_key: ""
  bucket: ""
  region: "" # e.g. 'us-east-1'

(add aws-sdk-s3 to Gemfile)
  gem "aws-sdk-s3", require: false

(S3-compatible object storage API)
(DigitalOcean Spaces 'endpoint')

digitalocean:
  service: S3
  endpoint: https://nyc3.digitaloceanspaces.com
  access_key_id: ...
  secret_access_key: ...
  # ...and other options
#

#
azure:
  service: AzureStorage
  storage_account_name: ""
  storage_access_key: ""
  container: ""

(azure-storage-blob gem to Gemfile)
  gem "azure-storage-blob", "~> 2.0", require: false
#
google:
  service: GCS
  credentials: <%= Rails.root.join("path/to/keyfile.json") %>
  project: ""
  bucket: ""

(google-cloud-storage gem to Gemfile)
  gem "google-cloud-storage", "~> 1.11", require: false
#

-- Mirror Service
- Replicates uploads
- Deletes across two or more subordinate services

A mirror service is intended to be used temporarily 
  during a migration between services in production. 
  You can start mirroring to a new service, 
  copy pre-existing files from the old service to the new, 
  then go all-in on the new service.

(config.yml)
  s3_west_coast:
    service: S3
    access_key_id: ""
    secret_access_key: ""
    region: ""
    bucket: ""

  s3_east_coast:
    service: S3
    access_key_id: ""
    secret_access_key: ""
    region: ""
    bucket: ""

  production:
    service: Mirror
    primary: s3_east_coast
    mirrors:
      - s3_west_coast

It is recommended to use Rails.env in the bucket names 
  to further reduce the risk of 
  accidentally destroying production data.

  amazon:
    service: S3
    # ...
    bucket: your_own_bucket-<%= Rails.env %>

  google:
    service: GCS
    # ...
    bucket: your_own_bucket-<%= Rails.env %>

  azure:
    service: AzureStorage
    # ...
    container: your_container_name-<%= Rails.env %>


--- Choosing a service ---

During development...
  (config/environments/development.rb)

  # Store files locally.
  config.active_storage.service = :local

During testing...
  (config/environments/test.rb)

  # Store uploaded files on the local file system 
    in a temporary directory.
  config.active_storage.service = :test

During production...
  (config/environments/production.rb)

  # Store files on Amazon S3.
    config.active_storage.service = :amazon

--- Methods ---

active_storage_blobs
  Stores data about uploaded files, 
  such as filename and content type.

active_storage_attachments
  A polymorphic join table that connects your models to blobs. 
  If your model's class name changes, you will need to 
  run a migration on this table to update the underlying 
  record_type to your model's new class name.

active_storage_variant_records
  If variant tracking is enabled, 
  stores records for each variant that has been generated.

- has_many_attached -
  one-to-many relationship between records and files.
  Each record can have many files attached to it.

example:
  
  Model:
    class Message < ApplicationRecord
      has_many_attached :images
    end

  Controller:
    class MessagesController < ApplicationController
      def create
        message = Message.create!(message_params)
        redirect_to message
      end

      private
        def message_params
          params.require(:message).permit
          (:title, :content, images: [])
        end
    end

images.attach - add new images to existing message:
  @message.images.attach(params[:images])

images.attached? - has any images?  
  @message.images.attached?

.variant

  - resize_to_limit: [100, 100]
  - resize_to_fit: [100, 100]
  - resize_to_fill: [100, 100]
  - resize_and_pad: [100, 100]
  - crop: [20, 50, 300, 300]
  - rotate: 90

  #
  has_many_attached :images do |attachable|
    attachable.variant :thumb, resize_to_limit: [100, 100]
  end
  #

  another example:
  <%= image_tag user.avatar.variant(resize_to_limit: [100, 100]) %>

Prevent uploaded image from being lost if validation fails
  <%= form.hidden_field :avatar, value: @user.avatar.signed_id if @user.avatar.attached? %>
  <%= form.file_field :avatar, direct_upload: true %>

.purge - deletes blob and file from storage service
  # Synchronously destroy the avatar 
    and actual resource files.
  user.avatar.purge

  # Destroy the associated models 
    and actual resource files async, via Active Job.
  user.avatar.purge_later

  (If your files require a higher level of protection 
  consider implementing Authenticated Controllers.)

.representation - display image variant/preview
  Some file formats can't be previewed out of the box,
  like word docs. So check .representable? first.
  You may want to link_to instead in that case.

  #
  <ul>
    <% @message.files.each do |file| %>
      <li>
        <% if file.representable? %>
          <%= image_tag file.representation(resize_to_limit: [100, 100]) %>
        <% else %>
          <%= link_to rails_blob_path(file, disposition: "attachment") do %>
            <%= image_tag "placeholder.png", alt: "Download file" %>
          <% end %>
        <% end %>
      </li>
    <% end %>
  </ul>
  #

  Another example:

  image_tag file.representation(resize_to_limit: [100, 100])