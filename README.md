# Linux File System Structure

## 1. / (Root Directory)

- Top-level directory in the file system hierarchy.
- All other directories and files are under the root directory.

## 2. /bin (Binary)

- Essential binary executables (commands) for system recovery.
- Common commands like `ls`, `cp`, `mv` are stored here.

## 3. /boot

- Contains files for the system's bootloader.
- Kernel images, initrd (initial RAM disk), and bootloader config files.

## 4. /dev (Device)

- Contains device files representing and allowing communication with devices.

## 5. /etc (Etcetera)

- Configuration files for system-wide and user-specific settings.
- Crucial system configuration files are found here.

## 6. /home

- Home directories for individual users.
- Personal files and configurations for each user.

## 7. /lib (Library)

- Essential shared libraries needed by system binaries.
- May include kernel modules.

## 8. /media

- Mount points for removable media (USB drives, external hard disks).

## 9. /mnt (Mount)

- Directory for temporarily mounting filesystems.

## 10. /opt (Optional)

- Contains additional software packages installed on the system.

## 11. /proc (Process)

- Virtual file system providing information about processes and kernel parameters.

## 12. /root

- Home directory for the root user.
- Root user's configuration files and personal files.

## 13. /run

- Temporary filesystem holding runtime information since the last boot.

## 14. /sbin (System Binary)

- Essential system binaries for system administration.

## 15. /srv (Service)

- Contains data for services provided by the system.

## 16. /sys (System)

- Virtual file system exposing information and configuration settings about the kernel.

## 17. /tmp (Temporary)

- Directory for temporary files created by the system and users.

## 18. /usr (Unix System Resources)

- Contains user binaries, libraries, and documentation.
- Bulk of installed software and user-related files.

## 19. /var (Variable)

- Contains variable files, data that may change frequently during normal system operation.
- Examples include log files (`/var/log`), spool files (`/var/spool`), and temporary files (`/var/tmp`).




# File Permission


File permissions in Linux are a fundamental aspect of the operating system's security model. They define who can access a file or directory, and what actions (read, write, execute) they are allowed to perform. Each file or directory has three sets of permissions: one for the owner, one for the group, and one for others.

Here's a breakdown of file permissions in Linux:

### Permission Types:

1. **Read (`r`):**
   - Allows viewing the contents of a file.
   - For directories, allows listing the contents.

2. **Write (`w`):**
   - Allows modifying the contents of a file.
   - For directories, allows creating, deleting, and renaming files within the directory.

3. **Execute (`x`):**
   - For regular files: allows executing the file if it is a program or script.
   - For directories: allows entering the directory and accessing files inside.

### Permission Groups:

1. **Owner (`u`):**
   - The user who owns the file or directory.

2. **Group (`g`):**
   - The group associated with the file or directory.
   - All users in the group have these permissions.

3. **Others (`o`):**
   - All other users who are not the owner or in the group.

### Viewing Permissions:

The `ls` command with the `-l` option shows detailed file information, including permissions:

```bash
ls -l filename
```

The output looks like this:

```bash
-rw-r--r-- 1 user group 4096 Jan 1 12:34 filename
```

In this example:

- `-rw-r--r--`: The permission string.
- `1`: The number of hard links.
- `user`: The owner of the file.
- `group`: The group associated with the file.
- `4096`: The file size in bytes.
- `Jan 1 12:34`: The modification date and time.
- `filename`: The name of the file.

### Modifying Permissions:

The `chmod` command is used to change file permissions.

```bash
chmod permissions filename
```

- Example: Give read, write, and execute permissions to the owner, and read-only to others.

  ```bash
  chmod u+rwx,o+r filename
  ```

### Changing Ownership:

The `chown` command is used to change file ownership.

```bash
chown owner:group filename
```

- Example: Change the owner to "user1" and the group to "group1".

  ```bash
  chown user1:group1 filename
  ```

### Special Permissions:

There are also special permissions and attributes such as the Set User ID (`suid`), Set Group ID (`sgid`), and the sticky bit.

- `suid`: Allows a program to be executed with the permissions of the owner.
- `sgid`: Allows a program to be executed with the permissions of the group.
- Sticky bit: Prevents users from deleting or renaming each other's files in a common directory.

```bash
chmod +s filename   # Set suid/sgid
chmod +t directory  # Set sticky bit
```
