# backup-google-docs

Google Apps Script that exports all your Google Docs/Sheets/Slides into docx/xlsx/pptx files and PDFs in a folder in your Google Drive.

## About this script

For each file, both an Office file (docx/xlsx/pptx) and a PDF are generated.
All the Office files and PDFs are combined into a single zip file that's placed in the backup folder.
The zip file will be given a name such as `GoogleDocs-2020-04-01--10:30.zip`.

The script does not delete old zip files.
You'll need to take care of that yourself if you don't want the number of zips to grow forever.

Only files that you own (as opposed to files others have shared with you) will be backed up.
Remove the `file.getOwner()` check from the `backupAll` method if you want to change that.

## Limitations

Google's export API has a file size limit of 10MB.
If the exported form of a particular document is larger than that, this script will not be able to back it up.

## Short instructions

1. Create a new [Google Apps Script](https://script.google.com/) project and copy the [GoogleDocsBackup.gs script](GoogleDocsBackup.gs) file into it.

2. In the script, replace INSERT_FOLDER_ID_HERE with the ID of the folder you want backups to be placed in.

3. Run the `backupAll` function.
You'll probably want to create a trigger to run it on a schedule (e.g. nightly).

## Long instructions

If you'd like step-by-step setup instructions, see this post: http://brokensandals.net/google-docs-backup