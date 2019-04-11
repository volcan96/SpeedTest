[![Build Status](https://travis-ci.org/taganaka/SpeedTest.svg?branch=master)](https://travis-ci.org/taganaka/SpeedTest)

# SpeedTest++

Yet another unofficial speedtest.net client cli interface. 

volcan96: This is based on https://github.com/taganaka/SpeedTest but adds output to a single line, making writing to a file easier.

It supports the new (undocumented) raw TCP protocol for better accuracy.

## Features

1. Best server discovery based on speed and distance from you.

2. Line type discovery to select the best test profile based on your line speed.

3. Aggressive multi-threading program in order to saturate your bandwidth quickly.

4. Test supported: Ping / Jitter / Download speed / Upload speed / Packet loss (UDP).

5. Provide a URL to the speedtest.net share results image using option --share

6. volcan96: This is based on https://github.com/taganaka/SpeedTest and adds output to a single line, making writing to a file easier.

## Installation

### Requirements

1. A modern C++ compiler
2. cmake
3. libcurl
4. libssl
5. libxml2

### On Mac OS X

```
$ brew install cmake
$ mkdir ~/cmake_build
$ cd ~/cmake_build
$ cmake -DCMAKE_BUILD_TYPE=Release  # you can also put options after -DCMAKE but no options works
$ make install
```

### On Ubuntu/Debian

```
$ sudo apt-get install build-essential libcurl4-openssl-dev libxml2-dev libssl-dev cmake
$ cd cmake_build
$ cmake -DCMAKE_BUILD_TYPE=Release ..
$ make install
```

## Usage

```
$ ./SpeedTest --help
SpeedTest++ version 1.8
Speedtest.net command line interface
Info: https://github.com/taganaka/SpeedTest
Author: Francesco Laurita <francesco.laurita@gmail.com>

Usage: ./SpeedTest  [--latency] [--quality] [--download] [--upload] [--share] [--help]
      [--test-server host:port] [--quality-server host:port] [--output verbose|text]
optional arguments:
  --help                      Show this message and exit
  --latency                   Perform latency test only
  --quality                   Perform quality test only. It includes latency test
  --download                  Perform download test only. It includes latency test
  --upload                    Perform upload test only. It includes latency test
  --share                     Generate and provide a URL to the speedtest.net share results image
  --test-server host:port     Run speed test against a specific server
  --quality-server host:port  Run line quality test against a specific server
  --output verbose|text       Set output type. Default: verbose
$
```
## Outputting to a file on MacOS
```
# pre-reqs: install homebrew and moreutils
$ mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew # https://docs.brew.sh/Installation
$ brew install moreutils #allows flexible timestamps
# nesxt line has 3 parts: 1) tells SpeedTest to run and output text 2) moreutils' ts to prepend a timestamp on Speedtest's output | writes/appends output to a file using tee (in this case to Google Drive
$ /usr/local/bin/SpeedTest --output text |  /usr/local/bin/ts '%Y-%m-%d %H:%M:%S,' | /usr/bin/tee -a /Users/chungus/Google\\ Drive/SpeedTestPlus.csv
```

## License

SpeedTest++ is available as open source program under the terms of the [MIT License](http://opensource.org/licenses/MIT).
