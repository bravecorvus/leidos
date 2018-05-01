# EC2 Ubuntu 16.04 + Apache Hello World Installation Script
### Andrew Lee
## Usage

Display Help Information:
```
./script -h
```

Display Script Information:
```
./script -v
```

Run script with default configurations:
```
./script
```

Modify the instance type such as `t2.medium`:
```
./script "t2.medium"
```

**Note: Running this script will be 99% automated except a single instance when installing updates. The prompt will notify the user that the configuration file changed between versions of some software. In this case, I have just pressed "Return" on the default option of keep installed configuration. However, I find it highly unlikely that changing this to be a different configuration will affect the program much.**

## Brief Description
This script is 99% automated except the aforementioned prompt to select whether to keep an unknown software's maintainers configuration defaults, or to leave the configuration default as that which comes pre-installed on Ubuntu.

The script ensures the following error cases are handled correctly:
1. `aws` program is not installed.
2. `aws configure` has not been run, and hence, no valid aws access id and key are not stored by the `aws` program.
3. The user does not have ssh public:private key combination generated via the command `ssh-keygen -t rsa` (used to run passwordless-ssh and minimize user input)

However, for expediency, the script does make a few assumptions:
1. It will assume any security group with the name "leidos" (if it already exists) was created for the sole purpose of this script  and contains the necessary permissions to run the `aws ec2` commands.
2. It will assume a key:value pair with the name "leidos" (if it already exists) was created for the sole purpose of this script and contains the necessary permissions to run the `aws ec2` commands.

In both cases, if such a credentials does not exist, the script will generate those for the user automatically.

(If either of the above assumptions are making the script fail, either rename the names of the security group/key-value pair in the script, or delete the previous entry in AWS console)
