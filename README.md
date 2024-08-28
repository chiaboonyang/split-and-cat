# split-and-cat

## Split The File
The split command splits the file into chunks of 1GB as denoted by the `--bytes` flag. The `-d` flag sets the names of the file chunks using numeric suffixes.

    split <file name> --bytes 1GB -d

After this command is performed, the directory should be populated with file chunks of size 1GB each. For example, splitting a file of size 13,905,249,504 bytes generates the following

x00 1000000000
x01 1000000000
x02 1000000000
x03 1000000000
x04 1000000000
x05 1000000000
x06 1000000000
x07 1000000000
x08 1000000000
x09 1000000000
x10 1000000000
x11 1000000000
x12 1000000000
x13 905249504


## Cat The File
The cat command concatenates the file chunks into a single file.
The command you need to 
