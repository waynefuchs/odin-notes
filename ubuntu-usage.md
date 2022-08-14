# Ubuntu Usage

## Text to Speech

The following sequence will read a webpage; for those times when you want to pre-review the content while you do something else. The pronunciation is pretty bad in some cases, so you still want to read, follow links, and study. But I've found some success in knowing what type of information is contained in a lesson.

1. `lynx -dump -nolist [URL] > blah.txt`
2. `cat blah.txt | pico2wave -w blah.wav`
3. `aplay blah.wav`