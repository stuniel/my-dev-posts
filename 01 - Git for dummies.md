#### How git works

- it stores references to **snapshots** of the data instead of list of file-based changes
- if there is no change in a file Git stores a **link** to the previous identical file
- it can be run locally because entire history of the project is stored on local disc in .git folder
- every clone is a full backup of all the data, each clone has a full history
- it’s impossible to change the contents of any file or directory without Git knowing about it because everything is **check-summed** before it is stored
- it's hard to loose changes because nearly all Git actions **add data** to the Git database

#### The 3 States

Git has three states:

- **modified** - you have changed something in your file
- **staged** - you have marked modified file to go into your next commit snapshot
- **commited** - you have stored the file in your local database

That gives us three main sections of a Git project:

- **working tree** - one version of files pulled out of the compressed database in git directory, ready to be used and modified
- **staging area** - also called index - file that stores information about what will go into your next commit
- **git directory** - this is where Git stores all the metadata and object database for your project
