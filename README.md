# image-dl
Python program for batch image downloading from various hosts (e.g. imagebam, imgbox, etc...).

### To Do
* [x] Single image downloading from a given URL
* [ ] Album/Gallery downloading
    * [x] imagebam
    * [x] imagevenue
    * [x] imgbox
    * [x] imgur
    * [x] someimage
    * [ ] upix
* Add real error handling
* Add concurrency for parallel downloading


## Installation
Download from Github and import `image_dl`.

### Dependencies
- [Requests](http://docs.python-requests.org/en/latest/)
```sh
>>> pip install requests
```
- [BeautifulSoup](http://www.crummy.com/software/BeautifulSoup/)
```sh
>>> pip install beautifulsoup4
```


## Usage

### Examples

#### Image
```python
# import
from image_dl import download_image

# required parameters
url = "<img_url>"
name = "<name>"

# download image to current directory
download_image(url, name)

# download image to "\img" directory
download_image(url, name, "img")
```

#### Album
See "To Do" section above for a list of valid `host` values.

```python
# import
from image_dl import download_album

# required parameters
url = "<album_url>"
name = "<name>"
host = "<host>" # (e.g. "imgur", "imgbox")

# download album to current directory
download_album(host, url, name)                      # ["<name>001.xxx", ...]

# download album to "\img" directory
download_album(host, url, name, "img")               # ["img\<name>001.xxx", ...]

# download with "_" delimiter
download_album(host, url, name, delim="_")           # ["<name>_001.xxx", ...]

# download with image numbers of length 5
download_album(host, url, name, digits=5)            # ["<name>00001.xxx", ...]

# download with image numbers starting at 17
download_album(host, url, name, number=17)           # ["<name>017.xxx", ...]

# download with all of the changes above:
download_album(host, url, name, "img", '_', 5, 17)   # ["img\<name>_00017.xxx", ...]
```

## License

MIT License.

See [LICENSE.txt](https://github.com/primeape91/image-dl/blob/master/LICENSE.txt) for more details.
