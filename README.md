# postgres2ramdisk
## Run your PostgreSQL in RAM

These utilities allow you to run Postgres in a ram disk. It's main purpose is to speed up test in environments like Rails.

For the moment only Mac OS is supported (either via macports or homebrew postgresql installs.)

##### DISCLAIMER: THIS IS NOT INTENDED TO BE RUN ON PRODUCTION ENVIRONMENTS
##### IF YOU RUIN (YOUR) IMPORTANT DATA, IT'S YOUR FAULT

## Installation

### Prerequisites

These install instructions assume you have:

1.  ```~/bin``` and ```~/opt``` dirs with ```~/bin``` already in your ```PATH```.
2.  An already working PostgreSQL install in either macports or homebrew.

### Install

(This are plain and overly simplistic instructions, you may want to customize this even further)

    mkdir ~/opt
    git clone https://github.com/luismreis/postgres2ramdisk
    cd ~/bin
    ln -s ~/opt/postgres2ramdisk/bin/* .

    cp ~/opt/postgres2ramdisk/etc/postgres-common{.sample,}

Open the file ```/opt/postgres2ramdisk/etc/postgres-common``` in your favorite editor and tune it according to
your preferences (ramdisk size, macports vs homebrew, postgresql version.)

### Caveat Emptor

_Please Backup your database before running the following steps for the first time._

### Usage

To copy your current running PostgreSQL database to ramdisk:

    postgres2ramdisk

Note that parts of this script are run with sudo, so, your password may be asked.

To get back to regular storage:

    unmount-postgres

This script copies the database back. You can easily comment the code on ```unmount-postgres``` to prevent it.
The same note about password requests above also applies here.

## Other Tricks

Your new shiny ramdisk will be shown on your desktop. To use a custom icon:

1.  Get an .icns file
2.  Copy it to $MOUNTPOINT

    1.   E.g., ```sudo cp PostgreSQL.icns /opt/local/var/db/postgresql9x/.VolumeIcon.icns```

## Reference

Several articles, blog posts and man pages were consulted to produce these scripts. Here are the most relevant:

*   http://blog.vergiss-blackjack.de/2011/02/run-postgresql-in-a-ram-disk/
*   http://osxdaily.com/2007/03/23/create-a-ram-disk-in-mac-os-x/
*   http://stackoverflow.com/questions/369758/how-to-trim-whitespace-from-bash-variable
*   https://discussions.apple.com/thread/773234
*   http://apple.stackexchange.com/questions/6707/how-to-stop-os-x-from-writing-spotlight-and-trash-files-to-memory-cards-and-usb

## License

(The MIT License)

Copyright (c) 2013 Luis Reis

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
