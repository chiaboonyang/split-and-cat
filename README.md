# split-and-cat

Transferring files through USB and Citrix sometimes results in corrupted copies or timeout problems, and this problem is exacerbated when the files are large. To reduce the occurrences of such problems, I recommend to split large files into smaller chunks at the source, copying on the transfer medium (via robocopy if possible), and then concatenating the chunks into the original file at the target.

In this example, a large file of 13,905,249,504 bytes is used.

## Split The File
The `split` command splits the large file into chunks of 1GB as denoted by the `--bytes` flag. The `-d` flag sets the names of the file chunks using numeric suffixes.

    split filename1.tar --bytes 1GB -d

The command populates the current directory with an additional 14 file chunks. The first 13 chunks are 1,000,000,000 bytes each while the last chunk is 905,249,504 bytes.The file chunks are named sequentially, from `x00` to `x13`.

## Copy The File Chunks
Use GUI or `robocopy` to copy the file chunks onto the transfer medium.

## Cat The File
The `cat` command concatenate files and print on the standard output. This command rebuilds the original file from the chunks for this specific example.

    cat x00 x01 x02 x03 x04 x05 x06 x07 x08 x09 x10 x11 x12 x13 > filename2.tar

Alternatively, you can use the following command and adapt it to avoid manually typing out the names of the file chunks.

    cat x0{0..9} x1{0..3} > filename2.tar

## Verification
Use `sha256sum` to compute and check SHA256 message digest of both files. The two checksums should be identical.

    sha256sum filename1.tar filename2.tar
