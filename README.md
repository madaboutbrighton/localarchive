# localarchive

A bash script to archive files from one location to another.

Ideally suited to media items such a photos, which can be archived according to the date that they were taken. The date is taken from the EXIF information, or as a last resort, the creation date of the file.

DEST_FOLDER, if it doesn't already exist, will be created. It may contain date format codes, such as %Y, %m %d, %h, %m, %s. For example "my/archive/%Y/%m" -> "my/archive/1994/07". The format codes are applied to the date taken or creation date of each file.

## Usage

localarchive SOURCE_FOLDER DEST_FOLDER