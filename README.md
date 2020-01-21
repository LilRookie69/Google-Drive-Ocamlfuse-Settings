# Google-Drive-Ocamlfuse-Settings

# Step 1
```
mkdir -p ~/folder_name
sudo chmod -R 777 ~/folder_name
```

# step 2
```
sudo add-apt-repository ppa:alessandro-strada/ppa --yes
sudo apt -y install google-drive-ocamlfuse && google-drive-ocamlfuse
```

# step 3

create file google drive on /etc/bin 
```
nano /etc/bin/gdrive
```
with value
```
#!/bin/bash
su our_username -l -c "google-drive-ocamlfuse -label $1 $*"
exit 0
```
set permission
```
chmod +x gdrive
```

# step 4
edit fstab
```
nano /etc/fstab
```
with value
```
gdfuse#default /home/rdanang/gdrive fuse uid=1000,gid=1000,allow_other,user,auto,_netdev 0  0
```

# step 5
edit /etc/fuse.conf
```
nano /etc/fuse.conf
```
with value
```
# Allow non-root users to specify the allow_other or allow_root mount options.
user_allow_other
```

# step 6
init the google drive ocamlfuse folder
````
google-drive-ocamlfuse
sh -c "google-drive-ocamlfuse ~/gdrive"
```
