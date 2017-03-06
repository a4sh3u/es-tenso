# Elasticsearch Tensō - 転送
A little tool to export/import data from and to elasticsearch

## Testing
Right now there is no testsuite. We've tried the script with various ES 1.7.3, 2.3.3 and 5.2.2 with data ranging from 1MB to ~9GiB and up to 17 million documents

# Usage

Tensō requires at least Python 3.5

```
python3.5 tenso-1.0.pyz [-h] [--source_auth_user SOURCE_AUTH_USER]
                     [--source_auth_pass SOURCE_AUTH_PASS] [-cs CHUNK_SIZE]
                     [-st SCROLL_TIME] [--dest_auth_user DEST_AUTH_USER]
                     [--dest_auth_pass DEST_AUTH_PASS]
                     [--max_file_size MAX_FILE_SIZE] [-v]
                     source [destination]
```

# Example

## Export to file

For a simple dump to a file just use:
```
python3.5 tenso-1.0.pyz http://1.2.3.4:9200 
```
This will create a file with the pattern dump-%Y-%m-%d_%H-%M-%S.zip

If you'd like to specify the target file you can add the destination argument
```
python3.5 tenso-1.0.pyz http://1.2.3.4:9200 mydump.zip
```

## Import from file
Starting from our export example above we would like to import the data in mydump.zip to our local development machine

```
python3.5 tenso-1.0.pyz mydump.zip http://localhost:9200
```

## Clone 
The same as above could also be achieved in one step using a direct clone

```
python3.5 tenso-1.0.pyz http://1.2.3.4:9200 http://localhost:9200
```


# License

MIT License

Copyright (c) 2017

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
