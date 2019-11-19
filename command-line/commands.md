# Commands

## cat

- can display contents of a file
- can combine "concatenate" two files
- can copy existing files into a new blank file

## echo

- display a string to the command console/terminal

## find

- can list all matches of a file search
- ex: `find . -name package.json`
- the above would find all locations of `package.json` inside the current folder and its subdirectories

- to find by extension (in this example all .md files):

`find . -name "*.md"`

## Grep

`grep "text string to search for" filename`

- `grep -i "require" app.js` would locate all `require()` statements inside an Express app file, for example.
- the `-i` flag is case insensitive
- adding `-c` would yield a numeric count of all the matches

## ls

- lists files and directories for the current/or specified directory

## mkdir

- creates a new empty directory

## mv

- moves a file or set of files to a new directory

`mv /test/README.md ./README.md`

## pwd

- present working directory ("the current directory" you are in)

## rm

- removes a file
- in order to remove a directory, pass the `-rf` flags to force write-protected files and recursively remove directory and its files

## rmdir

- removes directory only if it's empty

## tail

- displays the end of a file (by default, the last 10 lines)
- adding an optional `-n` flag with an integer will display the last (included integer amount) of lines
- for example: `tail -n 25 app.js` would show the last 25 lines of `app.js`

## touch

- creates an empty file, different than `cat` as `touch` will always yield a new empty file, whereas `cat` will concatenate existing content

## wget

- download files from specified url
- will have to install it via homebrew or package manager

[source1](https://medium.com/better-programming/here-are-11-console-commands-every-developer-should-know-54e348ef22fa)
