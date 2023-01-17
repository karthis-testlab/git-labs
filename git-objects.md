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

## Blob (Binary Long Object)

A Git blob is the object type used to store the contents of each file in a repository as binary data, along with the size of the data and a label indicating the object type. Blob is stored in Git's object database, which is located in the ``` .git/objects/ ``` in the root directory of the project repository.

Every blob in the git is identified by the SHA-1 hash. The SHA-1 hash consists of 20 bytes and is usually represented by 40 characters in the hexadecimal format.

### Blob vs File

A blob in Git will contain the same data in a file. But the only difference is how they store it, the blob is stored in the Git object database and a file is stored on the filesystem. Along with file contain metadata and bolb doesn't.

## Tree