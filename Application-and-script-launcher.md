# Application and script launcher Plugin
--------------------------------------------

The application and script launcher plugin allows you to execute bash commands and start bash scripts.

### Application launcher

The application launcher allows you to call bash applications or commands (with parameters) from *guh*. Once, the application started, the running state will change to true, if the application is finished, the running state will change to false.

#### Example

An example command could be [espeak](http://linux.die.net/man/1/espeak). (`apt-get install espeak`)

     espeak -v en "Chuck Norris is using gooe" # gooe = guh pronounced correctly
  
### Bash script launcher

The bashscript launcher allows you to call bash script (with parameters) from *guh*. Once, the script is running, the running State will change to true, if the script is finished, the running State will change to false.

#### Example
An example for a very usefull script could be a backup scrip like following `backup.sh` script

    #!/bin/sh
    # Directories to backup...
    backup_files="/home /etc /root /opt /var/www /var/lib/jenkins"
    
    # Destination of the backup...
    dest="/mnt/backup"
    
    # Create archive filename...
    day=$(date +%Y%m%d)
    hostname="guh.guru"
    archive_file="$day-$hostname.tgz"
    
    # Print start status message...
    echo "Backing up $backup_files to $dest/$archive_file"
    date
    echo
    
    # Backup the files using tar.
    tar czf $dest/$archive_file $backup_files
    
    echo
    echo "Backup finished"
    date
    echo "==========================="
    echo "  DONE, have a nice day!   "
    echo "==========================="

Make shore the script is executable:

    $ chmod +x backup.sh

