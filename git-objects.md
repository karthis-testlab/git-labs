# Git Objects

Git is a **content-addressable filesystem**. *Content-addressable storage (CAS)* is a way to store fixed content as an object and provide fast access to that content.

### How CAS systems works, generally?

CAS systems generate a *unique key* for the content in the file using the *cryptographic hash function* (SHA-1). These unique keys are stored in the file system's directories and link to the physical storage of the content.

The reason behind that is if we attempt to store the same file, it will generate the same key. The reason behind that is if we attempt to store the same file, it will generate the same key. CAS system will create a new key when file is changed (or) modified. CAS system always ensure that the file is always unique and unchanged.

Git uses the same content-addressable system to maintain the file in a particular repository. In simple words, Git is a key-value data store, when we push (or) insert any kind of content into a repository. It'll return a unique key, later you can use the same key to retrieve that relevant content.

Git uses **object chaining** to link together various objects. They're;

1. Binary Long Object (Blob)
2. Tree
3. Commit
4. Annotated Tag

## Blob (Binary Long Object)

A Git blob is the object type used to store the contents of each file in a repository as binary data, along with the size of the data and a label indicating the object type. 

### Where are Git Blobs stored?

Blob object is stored in Git's object database, which is located in the ``` .git/objects/ ``` in the root directory of the project repository.

Every blob in the git is identified by the SHA-1 hash. The SHA-1 hash consists of 20 bytes and is usually represented by 40 characters in the hexadecimal format.

### Blob vs File

A blob in Git will contain the same data in a file. But the only difference is how they store it, the blob is stored in the Git object database and a file is stored on the filesystem. Along with file contain metadata and bolb doesn't.

## Tree

A Git tree object creates the hierarchy between files in a Git repository. We can use the Git tree object to create the relationship between directories and the files they contain.

```
In Git, the equivalent of a directory is a "tree". The tree is basically a directory listing referencing blobs as well as other trees.
```

Trees are identified by their SHA-1 hash, as well referring to these objects, either blobs or other trees happen via the SHA-1 hash of the objects.

### Tree vs Blobs

Git uses the tree to identify which tracked files correspond to the content stored in their bolbs. Blob is purely a file's binary content and it doesn't contain the information about file path and name of the filesystem. These informations are maintained by the Git tree. 

### Where are Git Tree object stored?

Tree object is stored in Git's object database, which is located in the ``` .git/objects/ ``` in the root directory of the project repository.

## Commit

In Git, **a snapshot of the working tree is a commit**. This means, storing all the files that existed at that time along with their contents. It also contains meta-data such as the information about the commiter, commit message, commit time and also having one (or) more parent commits of the previous snapshot, if any.

A commit object is created when we run ``` git commit ``` command.

### Where are Git Commit object stored?

Commit object is stored in Git's object database, which is located in the ``` .git/objects/ ``` in the root directory of the project repository.

For example, we can use the ``` git cat-file -p <object-hash> ``` command to provides the content of an object in a repoistory.

```
$ git cat-file -p b2f68f2cd4f275ae5d66352e8ee517676afa4b26
```
This would result in an output like the following:

```
tree 6634ea0aa87add3ab37e985d9d6454b6b04b85ea
parent 44ae4cea64fade91347a6779f2d50efe37bd2fd2
author Karthikeyan Rajendran <karthis.testlab@gmail.com> 1674111158 +0530
committer Karthikeyan Rajendran <karthis.testlab@gmail.com> 1674111158 +0530

Add tree object in the git-object.md file
```
As you can see, it contains the following information related to a commit:

1. Reference to the tree object;
2. Commit hash of parent(s);
3. Commit author;
4. Committer;
5. Commit message.

The command to provides the type of an object in a repoistory.

```
$ git cat-file -t b2f68f2cd4f275ae5d66352e8ee517676afa4b26

commit
```

## Annotated Tag

The annotated tag is a git object, which was stored in the git database. They're checksummed; contain the tagger name, email and date; have a tagging message; commit id and can be signed and verified with GNU Privacy Guard (GPG).

### Where are Git Annotated Tag object stored?

Annotated Tag object is stored in Git's object database, which is located in the ``` .git/objects/ ``` in the root directory of the project repository.

If we want create annotated tag, use ``` git tag ``` command along with the **-a** option. This will create a Git object.

```
git tag -a [-m <msg> | -F <file>] [tagname] [<commit_id>]
```
-m -> option used to specify the tag message
-F -> option used to the specifying a file with contains the tag message

if we to specify both -m (or) -F flag (options), in this case a editor will be opened. So, that we can type the tag message.

For Example;

```
git tag -a -m "MVP1.0 Release" v1.0
```

After executing the git tag command. If we want to see the tag detials such as the tagger name, date, tag message and commit detials we can use git show command for that.

```
git show [tagname]
```

To push the tag into the remote repository we can use the ``` git push ``` command.

**To transfer a single tag**, use the git push command and specify the remote name, such as origin, as well as the tag name.

```
git push [remote_name] [tagname]

For example,
git push origin v1.0
```

**To transfer all of tags**, use git push remote, followed by the tags option

```
git push [remote_name] [--tags]

For example,
git push origin --tags
```