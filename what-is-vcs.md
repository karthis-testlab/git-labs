# What is a “Version Control System” (VCS)?
Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.

## VCS Concept:

### Level 1 - Beginner - Standalone work

When we started storing the projects, some of their code was in different directories, so when a new version was created, we would simply create a new folder and copy the content there. Quite often such folders are named randomly, which results in us having one single project, but multiple versions of it. And it’s quite difficult to figure out when a specific version was created. Who was the last one who modified it? Yes, we can check this using the file properties. But we can’t able to track at the code line level in this approach.

### Level 2 - Network Share - Team Work

At this level, we can use the centre of the building system features of the operating system, which implies sharing the folder via the network. Let’s imagine that we want to share the code which was written by me with the team. In this, we can share the folder in the network. Both the team and me can edit the code at the same time in the defined network location. The problem here is the last person to save the file overrides the changes made by the other person.

### Level 3 - Cloud - Standalone / Team Work

We can store and maintain our files in the cloud services like Dropbox, OneDrive, Google Driver or Yandex disk, but we’ll still be faced issues in file synchronization. This means that more people are modifying the same file at the same time. The system cannot understand which modifications are correct and which we should not. The changes are correct in which can be deleted. This workflow is not suitable for one who writes or maintains code. It may be applicable to save Microsoft Word Documents or Powerpoint.

Then, what could be the goal of the version control system? What makes a good version control system and what it must be able to do?

## VCS Goals
1. Backup and Restore
2. Synchronization
3. Undo
4. Track Changes and Ownership
5. Sandboxing
6. Branching

## The Problem of File-Sharing

The common problem of the all version control system is, how the team effectively collaborate with each other without destroying or overwriting another persons code. Because in the file-sharing we can easily overwrite each other’s file or work accidentally in the repository.

Consider the scenario, Suppose we have two co-workers, Harry and Sally. They each decide to edit the same repository file at the same time. If Harry saves his changes to the repository first, then it's possible that (a few moments later) Sally could accidentally overwrite them with her own new version of the file. While Harry's version of the file won't be lost forever (because the system remembers every change), any changes Harry made won't be present in Sally's newer version of the file, because she never saw Harry's changes to begin with. Harry's work is still effectively lost—or at least missing from the latest version of the file—and probably by accident. This is definitely a situation we want to avoid!