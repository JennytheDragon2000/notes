The manual simulation of `git add` involves creating a blob object for the file, which is a binary large object containing the file data. The SHA-1 hash of the blob object is calculated, which is then used as the name of the blob object in the Git object store.

Git prepends the string "blob " followed by the filesize, a null byte, and then the file content before calculating the SHA-1 hash. It seems like you are missing the null byte.

To manually simulate the `git add` command and create a blob object, you should follow these steps:

1. Concatenate the header (which consists of the keyword "blob", the file size, and a null byte) with the file content.
2. Calculate the SHA-1 hash of this concatenated string.
3. Compress the concatenated string using zlib and store it in the .git/objects directory, using the first two characters of the hash as the directory name and the rest of the hash as the file name.

Here is how you can do it:

```shell
# Step 1: Concatenate the header with the file content
printf 'blob %s\0' "$(wc -c < hello.txt)" > temp.txt
cat hello.txt >> temp.txt

# Step 2: Calculate the SHA-1 hash
hash=$(sha1sum temp.txt | awk '{print $1}')

# Step 3: Store the blob object in the Git object store
dir=".git/objects/${hash:0:2}"
file="${hash:2}"
mkdir -p "$dir"
gzip -c temp.txt > "${dir}/${file}"
```
- first two digits will become the directory name 
- ![[Pasted image 20231228131450.png]]

The `printf` command is used to create the header. The `%s\0` format specifier in the `printf` command is used to include a null byte. The `wc -c < hello.txt` command is used to get the size of the file. The `sha1sum` command is used to calculate the SHA-1 hash of the file. The `awk` command is used to extract the hash from the output of the `sha1sum` command. The `gzip` command is used to compress the file content before storing it [Source 8](https://git-scm.com/docs/hash-function-transition/en).

## What happens when adding multiple files?

When you add multiple files using `git add`, Git creates a blob object for each file, just like when you add a single file. It calculates a unique SHA-1 hash for each blob object and stores the blob objects in the Git object store. 

For each file you add, Git updates the index (also known as the staging area) with the file's path and the SHA-1 hash of the blob object. The index is a binary file (generally kept in .git/index) containing a sorted list of path names, each with permissions and the SHA-1 hash of a blob object; it describes a tree object representing the current version of the repository [Source 4](https://github.com/git-guides/git-add).

You can add multiple files at once by listing them one after the other, separated by a space:

```shell
git add file1.txt file2.txt file3.txt
```

Or you can use wildcard characters to add multiple files. For example, to add all text files in a directory:

```shell
git add *.txt
```

You can also add all the files in a specific folder:

```shell
git add folder/*
```

Or add all files in the repository (excluding those in your .gitignore file):

```shell
git add .
```

These commands will stage all matching files, making them ready for commit [Source 0](https://stackoverflow.com/questions/19576116/how-to-add-multiple-files-to-git-at-the-same-time), [Source 1](https://stackoverflow.com/questions/8412081/git-add-multiple-files-at-once), [Source 2](https://stackoverflow.com/questions/32074850/how-to-add-multiple-files-in-git-for-a-single-commit).

Remember, the `git add` command does not permanently store file changes in the repository; it only stages them for commit. After adding the files, you must run `git commit` to store the changes in the repository:

```shell
git commit -m "Your commit message"
```

This command creates a new commit object in the Git object store and moves the HEAD pointer to the new commit [Source 4](https://github.com/git-guides/git-add).