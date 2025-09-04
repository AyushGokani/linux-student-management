```bash
$ python -m venv venv
$ source ./venv/bin/activate
pip install -r requirements.txt
```

## Managing the "teacher" Group in Linux

To ensure that only users in the "teacher" group can run the student information management system, you'll need to create and manage this group in your Linux environment.

### 1. Create the "teacher" Group

To create a new user group named "teacher", use the following command:

```bash
sudo groupadd teacher
```

### 2. Add a User to the "teacher" Group

To add a user to the "teacher" group, use the following command (replace `username` with the actual username):

```bash
sudo usermod -aG teacher username
```

You can check if the user has been successfully added to the group by running:

```bash
groups username
```

### Check Current User's Groups

To check which groups the current user belongs to, you can use the `groups` command along with `whoami` to get the current username:

```bash
groups $(whoami)
```

This will list all the groups that the current user is a member of.

> **Note:** The user will need to log out and log back in for the group change to take effect.

### 3. Remove a User from the "teacher" Group

To remove a user from the "teacher" group, use the following command:

```bash
sudo gpasswd -d username teacher
```

This will remove the user from the "teacher" group, and the change will take effect immediately.

### 4. Delete the "teacher" Group

To delete the "teacher" group entirely, use the following command:

```bash
sudo groupdel teacher
```

> **Note:** Make sure no important users rely on this group before deletion.

## How to Run the Project

### Generate `basic_info.txt` from `student_list_orig.txt`

The first step is to convert the provided `student_list_orig.txt` into `basic_info.txt`.

```bash
python student_info_manager.py --generate-basic-info
```

This will read from `student_list_orig.txt` and output `basic_info.txt` in the format:

```
student_id | first_name | last_name | email_address
```

### Simulate New Student Academic Information

You can simulate new academic data either hourly or manually by running the simulation script:

```bash
python simulation.py --simulate
```

This will append new academic info to `academic_info.txt` in the following format:

```
student_id | course | grade_type | percentage | note
```

### Merge Basic and Academic Info

After gathering both basic and academic information, the following command will merge them into `student_info.txt`:

```bash
python student_info_manager.py --merge-info
```

This will create `student_info.txt` in the format:

```
student_id | first_name | last_name | email_address | course | grade_type | percentage | note
```