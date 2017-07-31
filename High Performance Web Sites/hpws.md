# Rule 1 Make Fewer HTTP Requests
* Image Maps
	* HTML: `<map>` and `<area>`
* CSS Sprites
	* CSS: background-position
* Inline Images
	* `<img src="data:image/gif;base64,...>`
* Combined Script and StyleSheets
	* Grunt
	* Gulp
	* Web pack 
# Rule 3 Add an Expires Header
* Expires: Date
* Cache-Control: max-age=seconds
* File with version number
# Rule 4 Gzip Components
* Content-Encoding: gzip (LZ77) / deflate (RFC 1950) / br (Brotli)
# Rule 6 Put Scripts at the Bottom
# Rule 10 Minify JavaScript
* remove comments
* obfuscation
* common tech
	* JS: true => 1, false => 0
	* CSS: #ffffff => #fff, 0px => 0
* Browser stop downloading when executing js
# Rule 11 Avoid Redirects
# Rule 12 Remove Duplicates Scripts
# Rule 5 Put Stylesheets at the Top
* IE only ?
# Rule 8 Make JavaScript and CSS External
# Rule 7 Avoid CSS Expressions
# Rule 14 Make Ajax Cacheable 

# Rule 13 Configure ETags
* `ETag` and `If-None-Match`
* `ETag` in different Server

# Rule 2 Use a Content Delivery Network
# Rule 9 Reduce DNS Lookups
