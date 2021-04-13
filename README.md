# Shup

Simple HTML parser in shell.

- Requires
	* POSIX shell
	* sed

## Usage

	
```sh
USAGE: shup [OPTIONS] ["FILTER1" "FILTER2" ...]
  -h                 show this help
  -v                 show version
  -r                 raw: last filter tag will not be shown
  -t                 text: no tags will be shown
  -o   "string"      specify output indentation

FILTER FORMAT: "<tagname>"  or  "<tagname>[<search string>]"
    the search string should be present in the tag line
  EXAMPLE
    to match all div tags
         shup "div"
    to match div tags with some string
         shup "div[Qynugf]"
    will match : <div class="Qynugf">

    The string could be present anywhere inside the tags body <.>
    Patterns can be specified in the string using shell patterns
         shup "div[Qy?*[!h]f]"
 When no filters applied, shup will only format the HTML
```

## Example

```sh
curl -s "www.gnu.org" | shup -r "body" "div[inner]" "ul" "li[[pP]hilo]" "a"
```
