# FlatFS

Install fuse and sqlite3 library before running the file system.

command to build FlatFS: g++ flatFS.cpp  -o flatFS 'pkg-config fuse --cflags --libs' -l sqlite3 

(check below link for the error " pkg-config --cflags opencv: No such file or directory " - https://stackoverflow.com/questions/20625096/pkg-config-cflags-opencv-no-such-file-or-directory )

command to run FlatFS: ./flatFS -f test (create a directory named test to mount flatfs)

NOTE: Please ignore errors shown in the Mounted directory(test) while executing commands (Example: while executing touch command it may show some error but it is from the HFS - just ignore it). Only consider error log in terminal where you run the FlatFS. This terminal will also show some log info. 

At the start, program will ask for the database location. Please give the location with database name (sql.db). Please allow read and write permissions for the database location path. Database location must be specified from the root.(database location example: /home/navin/Desktop/sql.db)

Features Implemented: (Open the Mounted Directory - "test" in Terminal and execute the commands)

1. Creating files using "touch" command (example: touch 'unit1:change1,unit2:change2')
2. Use "ls ?" to list all files created.
3. Searching using "ls ?" command (example: ls '?unit1:change1'). You can also list all files by simply specifying "ls ?" (performs similar to "ls")
4. Add spec to files using "mv" command (example: mv 'unit1:change1,unit2:change2' '+unit3:change3')
5. Delete spec from the files using "mv" command (example: mv 'unit1:change1,unit2:change2,unit3:change3' '_unit3:change3')
6. Replace spec for a file using "mv" command (example: mv 'unit1:change1,unit2:change2,unit3:change3' '<unit5:change5')
7. Adding spec to multiple files using "mv" command (example: mv '?unit5:change5' '+unit7:change7'). This command will search for all files containg spec 'unit5:change5' and add the spec 'unit7:change7' if not exist.
8. Deleteing spec from multiple files using "mv" command (example: mv '?unit5:change5' '_unit7:change7'). This command will search for all files containg spec 'unit5:change5' and delete the spec 'unit7:change7' if exist.
