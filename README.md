# git-reset-head-file-recover
A Python script to try recover lost files following a mistaken 'git reset --hard' command.

## Disclaimer

This software **does not, in any way possible** promise to recover any of your files. It simply provides a mechanism for which to **try** and recover files yet to be rmeoved by the `git` garbage collector. 

The author takes **no responsibility or liability** for any damages to files, software or hardware caused as a result of using this software.

## Credits

This project is heavily based on an existing Python script provided by user 'Boy' over at [StackOverflow](http://stackoverflow.com/a/20997627).

## Usage

1. Ask Git to list all "unreachable blobs" (i.e. files not added/commit and now unreachable) and pipe this to a file.

        git fsck --cache --unreachable $(git for-each-ref --format="%(objectname)") > allhashes.txt

2. Run the Python script.

        python recover_git_blobs.py allhashes.txt

3. The script will export a collection of files containing the contents of each cached "unreachable blob". The user can then serach through the contents of these files in order to try and find the file they wish to recover.
