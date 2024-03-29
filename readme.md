# binwrap
Convenience wrappers for your command line favorites. Simply put, CLIs are decorated with
subcommands to do things like:

```bash
$ curl finlink https://google.com
```

_instead of:_

```bash
$ curl https://google.com -s -L -I -o /dev/null -w "%{http_code}: %{url_effective}\\n"
```

## Installation
Wrappers must be used at the `.bash_profile` level. You can simply copy and paste there or you
can use a more modular approach:

In `.bash_profile` source your modular dotfiles:
```bash
# Load dotfiles.
for file in ~/.{exports,aliases,wrappers,functions,sources}; do
  [ -r "$file" ] && [ -f "$file" ] && source "$file";
done;
unset file;
```

And then simply use `curl` to add wrappers you would like to use into `~/.wrappers`:

```bash
$ curl https://raw.githubusercontent.com/rockymadden/binwrap/master/curl > ~/.wrappers && \
curl https://raw.githubusercontent.com/rockymadden/binwrap/master/docker >> ~/.wrappers && \
curl https://raw.githubusercontent.com/rockymadden/binwrap/master/ssh >> ~/.wrappers && \
curl https://raw.githubusercontent.com/rockymadden/binwrap/master/vegeta >> ~/.wrappers && \
curl https://raw.githubusercontent.com/rockymadden/binwrap/master/wget >> ~/.wrappers
```

## Usage
To see the available binwrap subcommands, and their usage, execute the `binwrap` subcommand on any
wrapped CLI:
```bash
$ curl binwrap
$ docker binwrap
$ ssh binwrap
$ vegeta binwrap
$ wget binwrap
```

## License
```
The MIT License (MIT)

Copyright (c) 2015 Rocky Madden (https://rockymadden.com/)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
