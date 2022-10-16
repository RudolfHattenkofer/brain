## Option 1

gcsfs

[GitHub - RaRe-Technologies/smart_open: Utils for streaming large files (S3, HDFS, gzip, bz2...)](https://github.com/RaRe-Technologies/smart_open)

## Option 2

[Add an API method to give us a streaming file object · Issue #29 · googleapis/python-storage · GitHub](https://github.com/googleapis/python-storage/issues/29#issuecomment-459414827)

OK, looking at the underlying implementation in google-resumable-media, all that we actually expect of the file object is that it has a write method, which is then passed each chunk as it is downloaded.

You could therefore pass in an instance of your own class which wrapped the underlying stream, e.g.:

from google.cloud.storage import Client

class ChunkParser(object):

def **init**(self, fileobj):

self._fileobj = fileobj

def write(self, chunk):

self._fileobj.write(chunk)

self.*do*something_with(chunk)

client = Client()

bucket = client.get*bucket('my*bucket_name')

blob = bucket.blob('my_blob.xml')'

with open('my*blob.xml', 'wb') as blob*file:

parser = ChunkParser(blob_file)

blob.download*to*file(parser)



