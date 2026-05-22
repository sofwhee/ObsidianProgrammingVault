Dependency Injection

Instead of creating a dependency

```C#
private ClassB _classB;

public void SetDependencies()
{
	_classB = Singleton.Instance.ClassB;
}
```

The class passes it to you instead

```C#
private ClassB _classB;

public void Inject(ClassB classB)
{
	_classB = classB;
}
```

You can write it yourself, or use VContainer, or Modest Tree Zenject.
https://vcontainer.hadashikick.jp/

---

[From CodeAesthetic](https://www.youtube.com/watch?v=J1f5b4vcxCQ&t=623s)

When you pass something in to be used, we call it Injection.

Example: Business app where you can chat with coworkers.

You can send files through it.
The file gets uploaded to an **Attachment Service.**
It's responsible for **storing, retrieving, and processing attachments.**

We're gonna set this up with Dependency Injection.
![[Pasted image 20260506161624.png]]

![[Pasted image 20260506162010.png]]

Chat messages get sent to our Chat Service. Simple enough.
Attachments get uploaded to the Attachment Service. 

- There's an endpoint in our Note service - `/attachment/upload` - that the app connects to, and uploads a file.
- The attachment gets stored on the disk temporarily
- Then, it's processed in a few ways
	- Default storage location is an Amazon S3. It simply lets you upload files and pull them down.
	- 
- Then uploaded to its final destination

S3 Code:
![[Pasted image 20260506162521.png]]

Export class Storage:

Async upload:

This function / method basically does this:

Takes an attachment and an API access key for AWS, then uses those to approve credentials and uploads `this` to s3 using the function after this one. Then it returns the `attachment_id`.

- params:
- attachment: Attachment
- keys: access key id and secret access key
- colon, `Promise<string>` - (seems like it's the async payload and it returns string)
	- get an `attachment_id` using `uuidv4()`
	- create a new `AWS.Credentials` with access key
	- create a new `AWS.S3` by specifying api version
	- wait for the attachment to upload to s3 by calling our async method `upload_to_s3` with all relevant params
	- return the attachment id, somehow retrieved after that by `uuidv4()`


Async `upload_to_s3`:

This async function uploads a list of uploads to s3 based on the parameters given. (optionally including a preview upload)

This function / method basically does this:
- creates a main s3 upload object with parameters given
- that s3 upload object then returns a list of all uploads, which we store in a variable
- if a preview is possible, we create an s3 upload object for that, and add it to `uploads` list
- Finally, Promise all uploads with `await Promise.all(uploads)`
#### Details:
- params:
- s3: AWS.S3, `attachment_id`, `message_id`, `local_path`, `preview_local_path?`
- `Promise<void>` - (returns nothing this time)
	- defines a `main upload` by getting the return from `s3.upload`
		- params:
		- Bucket 'uploads'
		- Key `attachment_id`
		- Metadata: plug in the message id like so `'message_id': message_id`
		- Body: (filestream?) `fs.createReadStream(local_path)`
	- defines `uploads` plural? idk why... so it can do multiple things?
	- isn't that not something you're supposed to do?
		- `uploads = [ main_upload.promise() ]`
		- it makes a list of uploads by...?
		- calling the promise of the s3 upload we just defined as main upload?
		- what does the s3.upload promise do?
		- obviously it returns a list of uploads...
	- if we put in a `preview_local_path` parameter in this upload_to_s3 thing...
	- it defines a `preview_upload`
		- uses the same exact function, but the `createReadStream` uses `preview_local_path instead`
	- then it pushes `uploads.push(preview_upload.promise()`
	- which means it just added the preview upload to the uploads list
	- OHHH, it's saying that if what you're trying to upload has the ability to be previewed, then it uploads the preview of your file as well!
- waits to Promise.all(uploads)