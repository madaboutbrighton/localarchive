# localarchive

A bash script to archive files from one directory to another.

Ideally suited to media items such a photos, which can be archived according to the date that they were taken. The archive date is sourced from the EXIF information of each file.

## Usage

```bash
localarchive /foo/bar /my/archive
```
This would **copy** all files with a matching format extension from `/foo/bar` to `/my/archive`

```bash
localarchive /foo/bar /my/archive/%Y/%m
```
This would **copy**, for example, a photo from `/foo/bar` that has an EXIF date taken of 24th July 2019 to `/my/archive/2019/07`

```bash
localarchive -rm /foo/bar /my/archive/%Y
```
This would **move** all successfully processed files from `/foo/bar` and all its subdirectories  to `/my/archive` grouping them by year.

## Options

#### Source path

The directory containing the files to be archived. This is required.

#### Destination path

The directory containing the files to be archived. This is required. If it does not already exist, the destination path will be created.

It may contain date format codes, such as %Y, %m %d, %h, %m, %s. The format codes are applied using the date taken or creation date of each file.

#### Dry run `-n `

Perform a trial run with no changes actually being made. Verbose output will be shown printed to the terminal. Default is `0`

#### Formats `-f`

Only files with the specified file extensions will be processed. Default is `"jpg,jpeg,png,mp4,avi,wmv,m4v,mov"`

#### Move `-m `

Move each successfully processed file. Default is `0` where each successfully processed file is copied instead of moved.

#### Recursive `-r `

Subdirectories of the source path will be processed recursively. Default is `0` where only files immediately within the source path will be processed.

#### Verbose `-v `

Increase the amount of information printed to the terminal. Default is `0`