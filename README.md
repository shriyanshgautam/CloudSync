# CluodSync
build rich cloud-enabled apps that sync their data to a remote web service, making sure all your devices always stay in sync so that users can restore their data when installing your application on a new device. For situations where the volume of data is relatively light (less than a megabyte), like the user's preferences, notes, game high scores or other stats, the Backup API provides a lightweight solution.

Step 1: Register for Android Backup Service at https://developer.android.com/google/backup/signup.html?csw=1  its free.
        
        ->A single Backup Service Key is valid for only the application with which you register using the form below. If you have multiple applications for which you would like a Backup Service Key, then you must register each application to receive a unique Backup Service Key for each one.
        -> provide the package name while registering.
        -> note down the key and the meta-data tag
        -> 
Step 2: add android backup agent class name to application tag. Copy the meta-data tag as child of application tag.

Step 3: now create a class with same name as backup agent you gave in application tag and extend it through  BackupAgentHelper that is a helper class for creating backup agent.

Step 4:Override onCreate and use BackupHelper either  FileBackupHelper for or SharedPreferencesBackupHelper to backup file or shared preferences. provide file name or shared preference group as constructor argument as applicable.

Step 5: call addHelper method after creating backupHelper instances and give the key (string constant to save and retrieve the backup later) and helper instance as its argument.One FileBackupHelper handles all the files that you need to back up, and one SharedPreferencesBackupHelper handles all the shared preferencegroups you need backed up. 

Step 6: Request backup of data by creating instance of BackupManager and call its dataChanged() method. otifies the backup manager that there is data ready to be backed up to the cloud,without having to worry about causing excessive network activity as for multiple request backup occurs only once if not already done.


Restoring backup :
Typically you shouldn't ever have to manually request a restore, as it happens automatically when your application is installed on a device. However, if it is necessary to trigger a manual restore, just call the requestRestore() method.


