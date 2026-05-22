can't fix scorm file
they'll have to reupload it
They'll have to send us the new scorm file

I'll let them know it's an issue within the scorm file now.
idk who is managing their scorm files.

Can we request a new file. 
We don't manage or create SCORM for them.
we're just hosting their SCORM file


SCORM CLoud

app.cloud.scorm.com
- we use this host for scorm just like we use jw player for media
- we use API to send information for entire scorm
- we have a limit in the backend for only 2 gb, that's why they want us to upload it manually
	- this is because it would timeout due to how long it takes
	- so we use scorm cloud instead
- 2607 is chapter id -> go to database (phpMyAdmin) spe2024 -> scorm_cloud_id -> Copy it and paste it to scorm cloud library search by Course ID -> format for generated course id is course id_fileattachmentid_timestamp -> we will not be reuploading, just replacing the file with overwrite course files -> 1 - 2 hours -> prompts you to save by checking the checkbox and press save/okay and then redo the upload 

set up ide and ftp client and then let darryl know so she can send me the info to access server clusters. that's where site directories are and i can have access.