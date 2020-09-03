# localarchive

A bash script to archive files from one directory to another using the creation date of each file.

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

```bash
localarchive -f "jpg,jpeg" /foo/bar /my/archive
```
This would only process files with a `jpg` or `jpeg` file extension.

```bash
localarchive -fm -t "https://hooks.slack.com/services/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" /foo/bar /my/archive
```
This would process the files and post a message on a Slack channel using the specified Webhook URL when the processing starts and stops.

## Options

#### Source path

The directory containing the files to be archived. **This is required**.

#### Destination path

The directory where the files are to be archived to. **This is required**. If it does not already exist, the destination path will be created.

The path may contain date format codes, such as `%Y`, `%m`, `%d`, `%h`, `%m`, `%s`. The format codes are applied using the CreateDate, DateTimeOriginal, or FileModifyDate of each file.

#### Dry run `-n `

Perform a trial run with no changes actually being made. Verbose output will be shown printed to the terminal.

#### Formats `-f`

Only files with the specified file extensions will be processed. Default is `"jpg,jpeg,png,mp4,avi,wmv,m4v,mov,heic"`

#### Move `-m `

Move each successfully processed file. Without this flag being set, each successfully processed file is copied instead of moved.

#### Notify `-t `

Service to notify when script begins and completes. Currently supports a Slack Webhook URL. 

#### Recursive `-r `

Subdirectories of the source path will be processed recursively. Without this flag being set, only files immediately within the source path will be processed.

#### Verbose `-v `

Increase the amount of information printed to the terminal.