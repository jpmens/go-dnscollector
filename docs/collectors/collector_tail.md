# Collector: Tail

The tail collector enable to read DNS event from text files.
DNS servers log server can be followed; any type of server is supported!

* Read DNS events from the tail of text files
* Regex support

Enable the tail by provided the path of the file to follow

Options:

* `file-path` (string)
  > Specifies the path to the file that will be monitored.

* `time-layout` (string)
  > Specifies the layout format for time representation, following the layout numbers defined in https://golang.org/src/time format.go.

* `pattern-query` (string)
  > Specifies the regular expression pattern used to match queries.

* `pattern-reply` (string)
  > Specifies the regular expression pattern used to match replies.

* `chan-buffer-size` (int)
  > Specifies the maximum number of packets that can be buffered before discard additional packets.
  > Set to zero to use the default global value.

Defaults:

```yaml
- name: tailf
  tail:
    file-path: null
    time-layout: "2006-01-02T15:04:05.999999999Z07:00"
    pattern-query: "^(?P<timestamp>[^ ]*) (?P<identity>[^ ]*) (?P<qr>.*_QUERY) (?P<rcode>[^ ]*)
      (?P<queryip>[^ ]*) (?P<queryport>[^ ]*) (?P<family>[^ ]*) (?P<protocol>[^ ]*)
      (?P<length>[^ ]*)b (?P<domain>[^ ]*) (?P<qtype>[^ ]*) (?P<latency>[^ ]*)$"
    pattern-reply: "^(?P<timestamp>[^ ]*) (?P<identity>[^ ]*) (?P<qr>.*_RESPONSE) (?P<rcode>[^ ]*)
      (?P<queryip>[^ ]*) (?P<queryport>[^ ]*) (?P<family>[^ ]*) (?P<protocol>[^ ]*) (?P<length>[^ ]*)b
      (?P<domain>[^ ]*) (?P<qtype>[^ ]*) (?P<latency>[^ ]*)$"
    chan-buffer-size: 0
```
