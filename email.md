```
imapsync \
         --host1 HOST1               --user1 USER1 --passfile1 PASSFILE1 --ssl1 \
         --host2 HOST2 --port2 PORT2 --user2 USER2 --passfile2 PASSFILE2 --ssl2 \
         --prefix2 'Archive/' --folder 'MyFolder' \
         --justfoldersizes --dry \
         --showpasswords --timeout 5
```