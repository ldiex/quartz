# View Linux file permissions

The `ls` command along with its `-l` (for long listing) option will show you metadata about your Linux files, including the permissions set on the file.

```
$ ls -l

drwxr-xr-x. 4 root root    68 Jun 13 20:25 tuned
-rw-r--r--. 1 root root  4017 Feb 24  2022 vimrc
```

In this example, you see two different listings. The first field of the `ls -l` output is a group of metadata that includes the permissions on each file. Here are the components of the `vimrc` listing:

- File type: `-`
- Permission settings: `rw-r--r--`
- Extended attributes: dot (`.`)
- User owner: `root`
- Group owner: `root`

The fields "File type" and "Extended attributes" are outside the scope of this article, but in the featured output above, the `vimrc` file is a normal file, which is file type `-` (that is, no special type).

The `tuned` listing is for a `d`, or directory, type file. There are other file types as well, but these two are the most common. Available attributes are dependent on the filesystem format that the files are stored on. 

# Read file permissions

The interesting permissions from the `vimrc` listing are:

```
rw-r--r–
```

This string is actually an expression of three different sets of permissions:

- `rw-`
- `r--`
- `r--`

The first set of permissions applies to **the owner of the file**. The second set of permissions applies to **the user group that owns the file**. The third set of permissions is generally referred to as "**others**." All Linux files belong to an owner and a group.

When permissions and users are represented by letters, that is called symbolic mode. For users, `u` stands for user owner, `g` for group owner, and `o` for others. For permissions, `r` stands for read, `w` for write, and `x` for execute.

When the system is looking at a file's permissions to determine what information to provide you when you interact with a file, it runs through a series of checks:

1. It first checks to see whether you are the user that owns the file. If so, then you are granted the user owner's permissions, and no further checks will be completed.
2. If you are not the user that owns the file, next your group membership is validated to see whether you belong to the group that matches the group owner of the file. If so, then you're covered under the group owner field of permissions, and no further checks will be made.
3. "Others" permissions are applied when the account interacting with the file is neither the user owner nor in the group that owns the files. Or, to put it another way, the three fields are mutually exclusive: You can not be covered under more than one of the fields of permission settings on a file.

Permissions go beyond the different types of people that can interact with a file. Each user gets an expression that includes the three basic types of permissions. In the example above, the owner of the file is given the following permissions:

```
rw-
```

Each character in the expression indicates whether a specific permission is granted or not. In the example above, read (`r`) permission and write (`w`) permission have been granted on the file. However, the execute permission (`x`) is not granted, which is why there's a `-` sign in the expression. The permission in this field is disabled.

Consider the group owner's permissions in this example:

```
r--
```

The read (`r`) permission is granted to members of the group, but write and execute have both been disabled.

# The octal values
When Linux file permissions are represented by numbers, it's called *numeric mode*. In numeric mode, a three-digit value represents specific file permissions (for example, 744.) These are called *octal values*. The first digit is for owner permissions, the second digit is for group permissions, and the third is for other users. Each permission has a numeric value assigned to it:

- r (read): 4
- w (write): 2
- x (execute): 1

In the permission value 744, the first digit corresponds to the user, the second digit to the group, and the third digit to others. By adding up the value of each user classification, you can find the file permissions.

For example, a file might have read, write, and execute permissions for its owner, and only read permission for all other users. That looks like this:

- Owner: rwx = 4+2+1 = 7
- Group: r-- = 4+0+0 = 4
- Others: r-- = 4+0+0 = 4

The results produce the three-digit value 744.