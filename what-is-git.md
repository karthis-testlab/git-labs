# What is git?

Git is a **distributed version-control system** for maintaining a file system and specifically snapshots of that system.

The main work of Git is, tracking or monitoring the changes in source code. It helps the team to implement the proper collaboration structure.

Git is not only used to track the source code but it can be used to track or maintain changes in any set of formats.

## Git is a Persistent Map

The basic idea behind core Git is just a map. A simple structure that maps keys to values

## Values and Keys

1. Values are just any sequence of bytes. The content of text files or even binary files
2. We can give value to git and it will calculate a key for it, a SHA1 algorithm
3. Every piece of content has its own SHA-1 hash.
4. SHA-1 hashes are 20 bytes in a hexadecimal format so they are sequences of 40 hex digits. This will be the Git key to store this content in the map
5. We can also calculate the hash in the command line using a low-level plumbing command 

**git-hash-object** - Compute object ID and optionally creates a blob from a file. 

**SYNOPSIS**
```
git hash-object [-t <type>] [-w] [--path=<file>|--no-filters] [--stdin [--literally]] [--] <file>...

git hash-object [-t <type>] [-w] --stdin-paths [--no-filters]
```
**DESCRIPTION**

Computes the object ID value for an object with specified type with the contents of the named file (which can be outside of the work tree), and optionally writes the resulting object into the object database. Reports its object ID to its standard output. When "type" is not specified, it defaults to "blob".

**OPTIONS**

| Options Name | Description                                                                                                    |
| :---         | :---                                                                                                           |
| -t           | Specify the type (default: "blob").                                                                            |
| -w           | Actually write the object into the object database.                                                            |
| --stdin      | Read the object from standard input instead of from a file.                                                    |
| --stdin-paths| Read file names from the standard input, one per line, instead of from the  command-line.                                                                                                                   |

**Sample Code**

```
$ echo "Git Training"
Git Training

$ echo "Git Training" | git hash-object --stdin 
3cc284c5034d003b4877dfcde5b988ab2debaf2a
```
