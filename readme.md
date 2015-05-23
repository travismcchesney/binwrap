# binwrap
Convenience wrappers for your command line favorites. Simply put, CLI tools are decorated with convenience functions to do things like `curl finlink url` instead of `curl url -s -L -I -o /dev/null -w "%{http_code}: %{url_effective}\\n"`.

## Install
Wrappers must be used at the `.bash_profile` level. You can simply copy and paste there or you could use a more modular approach:

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
curl https://raw.githubusercontent.com/rockymadden/binwrap/master/curl >> ~/.wrappers
curl https://raw.githubusercontent.com/rockymadden/binwrap/master/docker >> ~/.wrappers
```

## cURL
__finlink:__ Returns the final status code and URL.
```bash
$ curl finlink http://example.com/301
200: http://example.com/200
```

```bash
$ curl finlink http://example.com/404
404: http://example.com/404
```

__follow:__ Returns each status code and URL until final resolution (inclusive).
```bash
$ curl follow http://example.com/301
301: http://example.com/301
302: http://example.com/302
200: http://example.com/200
```

## Docker

__bash:__ Connect to a running container interactively via bash.
```bash
$ docker bash container-name
```

__daemonize:__
```bash
$ docker daemonize base /bin/echo hello
```

__interact:__
```bash
$ docker interact base /bin/bash
```

__ip:__ Get a running container's IP address.
```bash
$ docker ip container-name
```

__rmall:__ Stop all running containers and remove them.
```bash
$ docker rmall
```

__rmiall:__ Stop all running containers and remove all images.
```bash
$ docker rmiall
```

__stopall:__ Stop all running containers.
```bash
$ docker stopall
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
