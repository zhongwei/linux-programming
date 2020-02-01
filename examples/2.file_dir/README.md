# File and Directory Operation

1. file_op

   ```shell
   cd file_op
   gcc stat.c
   ./a.out stat.c
   gcc access.c
   ./a.out access.c
   gcc chmod.c
   ./a.out chmod.c
   gcc truncate.c
   touch tmpfile
   l tmpfile
   ./a.out tmpfile 100
   l tmpfile
   rm tmpfile
   gcc link.c
   ./a.out link.c hard_link
   stat link.c hard_link
   rm hard_link
   gcc symlink.c
   ./a.out symlink.c sym_link
   cat sym_link
   rm sym_link
   gcc readlink.c
   ln -s a.out tmplink
   ./a.out tmplink
   rm tmplink
   gcc unlink.c
   ./a.out
   gcc rename.c
   gcc chown.c
   gcc ls-l.c
   ./a.out ls-l.c
   ```

2. dir_op

   ```shell
   cd dir_op
   gcc chdir.c
   mkdir mytest
   ./a.out mytest
   rm -rf mytest
   gcc mkdir.c
   ./a.out mytest 0
   rm -rf mytest
   gcc opendir.c
   ./a.out .
   gcc readdir.c
   ./a.out .
   ```

3. dup

   ```shell
   cd dup
   gcc dup.c
   touch a.txt
   ./a.out
   cat a.txt
   gcc dup2.c
   ./a.out
   cat a.txt
   gcc fc.c
   ./a.out

   ```
