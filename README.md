# NAME: Ryan David Prasad
# REG. NO.: 212224040282

# AWS Lab: Working with Amazon EBS


## Aim

To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

---

## Algorithm / Steps

1. Create a new Amazon EBS volume with a size of 1 GiB.
2. Select the same Availability Zone as the EC2 instance.
3. Attach the EBS volume to the EC2 instance using `/dev/sdb`.
4. Connect to the EC2 instance using AWS Systems Manager Session Manager.
5. Check the available storage using `df -h`.
6. Create an `ext3` file system on the EBS volume.
7. Create the `/mnt/data-store` directory.
8. Mount the EBS volume to `/mnt/data-store`.
9. Configure `/etc/fstab` for automatic mounting.
10. Verify that the EBS volume is successfully mounted.
11. Create `file.txt` inside the mounted EBS volume.
12. Verify the contents of the created file.
13. Create an EBS snapshot named `My Snapshot`.
14. Delete `file.txt` from the original EBS volume.
15. Create a new EBS volume from the snapshot.
16. Attach the restored volume to the EC2 instance using `/dev/sdc`.
17. Create the `/mnt/data-store2` directory.
18. Mount the restored volume to `/mnt/data-store2`.
19. Verify that `file.txt` has been successfully restored.

## Program

### 1. Check Available Storage

```bash
df -h
```

### 2. Create an ext3 File System

```bash
sudo mkfs -t ext3 /dev/sdb
```

### 3. Create a Mount Directory

```bash
sudo mkdir /mnt/data-store
```

### 4. Mount the EBS Volume

```bash
sudo mount /dev/sdb /mnt/data-store
```

### 5. Configure Automatic Mounting


cat /etc/fstab
```

### 7. Verify the Mounted Volume

```bash
df -h
```

### 8. Create a File in the EBS Volume

```bash
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```

### 9. Read the File

```bash
cat /mnt/data-store/file.txt
```
### 10. Delete the File

```bash
sudo rm /mnt/data-store/file.txt
```

### 11. Verify File Deletion

```bash
ls /mnt/data-store/
```

### 12. Create a Mount Directory for the Restored Volume

```bash
sudo mkdir /mnt/data-store2
```

### 13. Mount the Restored EBS Volume

```bash
sudo mount /dev/sdc /mnt/data-store2
```

### 14. Verify Snapshot Restoration

```bash

ls /mnt/data-store2/
```

Expected output:

```text
file.txt
```

---



## Outputs

<img width="1917" height="992" alt="Screenshot 2026-11-06 083001" src="https://github.com/user-attachments/assets/9c844ffc-fdb6-47bf-a575-dc1a7e6b350a" />
<img width="1917" height="995" alt="Screenshot 2026-11-06 083112" src="https://github.com/user-attachments/assets/5fb0a55e-66d0-4fb1-b885-77401b77a816" />
<img width="1917" height="642" alt="Screenshot 2026-11-06 083258" src="https://github.com/user-attachments/assets/3f55280e-35fa-40e0-a66c-2526dc25b7ad" />
<img width="1917" height="972" alt="Screenshot 2026-11-06 083436" src="https://github.com/user-attachments/assets/00c09be9-1153-46f4-9229-3cb31769285f" />
<img width="1917" height="992" alt="Screenshot 2026-11-06 084038" src="https://github.com/user-attachments/assets/3664f799-8414-43ff-ae6d-e0e051164a1d" />
<img width="1917" height="990" alt="Screenshot 2026-11-06 084112" src="https://github.com/user-attachments/assets/b5619b00-cfb7-4499-90c5-a061f2f0a5cc" />
<img width="1150" height="333" alt="Screenshot 2026-11-06 084147" src="https://github.com/user-attachments/assets/fc179f52-6fea-4519-a702-603f09a8e7c3" />






---

## Result

Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an `ext3` file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted `file.txt` was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.
