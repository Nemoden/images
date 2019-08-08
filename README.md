Fetches images from https://placeimg.com/ to use for development / testing / etc.

I grew tired of googling images whenever I do testing, so I decided that all I want is a simple script to kick off and get images of exactly the size I want for testing / development.
This script does just that.
The repo comes with built-in images samples in `std` directory. Whenever `./fetch` is called to fetch image(s), it will drop those into `gen` directory (if `--dir` options is not specified).
So, suppose you need a 1280x1024 for testing something on your brand new cool website. Instead of googling for such an image with this script you'd do `./fetch 1280x1024` and that's it. And if you need 10 images of the same size, that's as easy as `./fetch 1280x1024:10`

Note: the script is written in Python v 2.7 (since it's already installed on majority of Linux/MacOS machines by default), `urllib2` was used intentionally so that we don't require to pull down any dependencies.

### How to use

Simply run

    ./fetch WIDTHxHEIGHT[:CATEGORY][:FILTER][:NUMBER]

and the script will fetch images from https://placeimg.com/ into `gen` directory (by default, this options is configurable with `--dir` option.

Whole usage is:

    $ ./fetch --help
    usage: fetch [-h] [-d DIRECTORY] [SPECIFICATION [SPECIFICATION ...]]

    Fetches images from placeimg.com for testing while developing your beautiful app

        Available image categories are: 'animals', 'arch', 'nature', 'people', 'tech'
        Available image filters are:    'grayscale', 'sepia'

        Specification format is: WIDTHxHEIGHT[:CATEGORY][:FILTER][:NUMBER]

    positional arguments:
      SPECIFICATION         Specification

    optional arguments:
      -h, --help            show this help message and exit
      -d DIRECTORY, --dir DIRECTORY
                            Output directory

### Call samples

    $ ./fetch 600x400:PEOPLE:SEPIA:3 100x100:TECH 1200x800:SEPIA:2
    Written: gen/600x400_PEOPLE_SEPIA.jpg
    Written: gen/600x400_PEOPLE_SEPIA_1.jpg
    Written: gen/600x400_PEOPLE_SEPIA_2.jpg
    Written: gen/100x100_TECH.jpg
    Written: gen/1200x800_SEPIA.jpg
    Written: gen/1200x800_SEPIA_1.jpg

    $ ./fetch 600x400:TECH
    Written: gen/600x400_TECH.jpg

    $ ./fetch 600x400
    Written: gen/600x400.jpg
