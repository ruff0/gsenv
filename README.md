## gsenv - PHP multi-version management for MediaTemple (mt) GridService.

### Key features:

 * Inspired by [GSenv](https://github.com/benallfree/mampenv) and [rbenv](https://github.com/sstephenson/rbenv) 
 * Run GS-supporeted PHP versions directly from the command line
 * Support for `composer` too
 * Use project-specific versions of GS's PHP installations
 * PEAR? PECL? Oh yes, each GS version of PHP already has that

gsenv is here to help you make sure that your command line is running the same
version that your GS Pro sites running.

Simply put a `.phpversion` file in the root of your folder and have the peace
of mind of knowing that your PHP version on the command line matches the version
GS is running for your site. All from a code repository kept in your local
`.gsenv` folder.

## How It Works

gsenv operates on the per-user directory `~/.gsenv`. This directory
contains shim-style scripts that take over the `php` and `composer` commands
on the command line. It will make sure they are executed using the PHP version
specified in your project folder's `.phpversion` file, if one is present. Otherwise,
it will use the latest version of PHP supplied with GS.

Each GS PHP version is a stand-alone installation with its own binaries and configuration.

## Installation

### Basic GitHub Checkout

This will get you going with the latest version of gsenv and make it
easy to fork and contribute any changes back upstream.

1. Check out gsenv into `~/.gsenv`.

        $ cd
        $ git clone git://github.com/benallfree/gsenv.git .gsenv

2. Add `~/.gsenv/bin` to your `$PATH` for access to the `gsenv`
   command-line utility.

        $ echo 'export PATH="$HOME/.gsenv/bin:$PATH"' >> ~/.bash_profile

3. Add gsenv init to your shell to enable shims and autocompletion.

        $ echo 'eval "$(gsenv init -)"' >> ~/.bash_profile

4. Restart your shell so the path changes take effect. You can now
   begin using gsenv.

        $ source ~/.bash_profile

5. If all goes well, `which php` should indicate a `~/.gsenv/bin/php` path.

### Upgrading

If you've installed gsenv using the instructions above, you can
upgrade your installation at any time using git.

To upgrade to the latest development version of gsenv, use `git pull`:

    $ cd ~/.gsenv
    $ git pull

## Usage

Like `git`, the `gsenv` command delegates to subcommands based on its
first argument. The most common subcommands are:

### gsenv versions

List the local GS PHP versions installed.

    $ gsenv versions

## How to Anchor Your Project to a PHP Version

First, see what versions are available on yoru system. 

    $ gsenv versions

If you don't like any you see, visit the [GS Pro Downloads](http://www.GS.info/en/downloads/) section and download more.

Next, navigate to your project directory and create a `.phpversion` file.

    $ cd ~/my_project
    $ echo "5.5.10" > .phpversion

Now test the version.

    $ which php
    $ php --version

## Development

The gsenv source code is [hosted on
GitHub](https://github.com/benallfree/gsenv). It's clean, modular,
and easy to understand, even if you're not a
shell hacker.

### License

(The MIT license)

Copyright (c) 2014 Ben Allfree

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
