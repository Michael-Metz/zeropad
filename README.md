# Table of Contents
1. [Introduction](#introduction)
2. [Set Up & Installation](#setup-and-installation)
3. [Usage](#usage)
4. [Examples](#examples) 
5. [Caution](#caution)
6. [What Exactly The Script Does](#what-exactly-the-script-does)
7. [License](#license)

<a name="introduction"></a>
# Introduction
`zeropad` is a bash shell script that renames all files in the currenty directory to a zeropadded sequence

zeropadded squences allow each file name in a directory to use the same width. For example compare directoy `A`, containing a non zeropadded sequence, to directory `B`, which contains a zeropadded sequence.

```
A
+-- 1.jpg
+-- 2.jpg
+-- 3.jpg
+-- .
+-- .
+-- .
+-- 12321.jpg
```

```
B
+-- 00001.jpg
+-- 00002.jpg
+-- 00003.jpg
+-- .
+-- .
+-- .
+-- 12321.jpg
```

<a name="setup-and-installation"></a>
# Set Up & Installation
> The following installation instructions are done under the ubunutu 16.04 operating system.  All commands are excuted using terminal.

## 1. Install zeropad

##### Make a folder to store the scripts
```sh
$ mkdir -p $HOME/bin/michael-metz
```
##### Download the scripts and move them to `$HOME/bin/michael-metz`
```sh
$ # Clone the repo with git or download the scripts manually
$ git clone https://github.com/Michael-Metz/zeropad.git
$
$ # Move script to folder
$ mv zeropad/zeropad $HOME/bin/michael-metz/
$ rm -rf zeropad
```
##### Make the srcipt executable
```sh
$ sudo chmod -R +x $HOME/bin/michael-metz/
```
##### Add my scripts to your path in `.profile`
```sh
$ cd $HOME
$ sudo nano .profile
```
`nano` opens a terminal based text editor 

##### Add to your `.profile` 

```
#michael-metz scripts
export PATH="$HOME/bin/michael-metz:$PATH"
```
To save and exit the text editor, type `ctrl + x` followed by `y` then hit return

<a name="usage"></a>

# Usage

`zeropad [-p prepend-text] [-a append-text] [num-digits]`

### Parameters 
zeropad requires 1 parameter

1. **[num-digits]** : how many digits places the number should use. Integer value *0 < v < 16.*

### Optional Flags

1. **[-p prepend-text]** : text to add before the zeropadded number.
2. **[-a append-text]** &nbsp;: text to add after the zeropadded number.  Typically the extension of the file. ex. `-a .jpg`

<a name="examples"></a>
# Examples

Consider a directory `my-images` that contains the following files

```
my-images
+
|-- Gorilla.jpg
|-- Squille.jpg
|-- Tree.jpg
```

```sh
#command
cd my-images
zeropad -p nature_ -a .jpg 4

#results in
my-images
+
|-- nature_0000.jpg
|-- nature_0001.jpg
|-- nature_0002.jpg
```
<a name="caution"></a>
# Caution
`zeropad` loops through directory files alphabetically.  Thus renaming the files in alphabetical order.  Therefore be careful if you want your sequence to have a particular order in the end.

<a name="what-exactly-the-script-does"></a>
# What the scripts does
1. Counts how many files are in the directory
2. Checks if the this count can be represented in *n* digits
3. Loops through files alphabetically and renames them taking parameters and flags into consideration

<a name="license"></a>
# License

MIT License

Copyright (c) 2017 MIchael Metz

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
© 2017 GitHub, Inc.
