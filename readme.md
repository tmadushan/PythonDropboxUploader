# This is an outdated, unmaintained project

This project used to interact with Dropbox using its website. This is hacky, hard to maintain, and is no longer fully possibly as Dropbox sometimes serves CAPTCHAs on certain requests. Dropbox has had a complete Python API for a long time now. I'd recommend using that instead:

https://www.dropbox.com/developers/documentation/python

If you just want something that can quickly let you use Dropbox from a terminal, I'd recommend rclone:

https://rclone.org/

-----

# PythonDropboxUploader (dbupload)

A very small Python package which provides a function to easily maniupulate files stored on Dropbox. This does not use the official API and should probably not be used on any kind of production system.

# Usage

## Basic uploading

```python
from dbupload import DropboxConnection

conn = DropboxConnection("email@example.com", "password")
conn.upload_file("local_file.txt","/remote/path/","remote_file.txt")
```

## Directory Listing

```python
from dbupload import DropboxConnection

conn = DropboxConnection("email@example.com", "password")
print(conn.get_dir_list('/remote/path'))
```

## Downloading a file

```python
from dbupload import DropboxConnection

conn = DropboxConnection("email@example.com", "password")
conn.download_file("/remote/path","remote_file.txt","local_file.txt")
```

## Download all files in a directory

```python
from dbupload import DropboxConnection

conn = DropboxConnection("email@example.com", "password")

urls = conn.get_dir_list('/remote/path')

for filename in urls:
    conn.download_file_from_url(urls[filename], filename)
```

## Delete a file in a directory

```python
from dbupload import DropboxConnection

conn = DropboxConnection("email@example.com", "password")

urls = conn.delete_file('/remote/path', 'remote_file.txt')
```

## Delete a directory

```python
from dbupload import DropboxConnection

conn = DropboxConnection("email@example.com", "password")

urls = conn.delete_dir('/remote/path/dir_to_del')
```
