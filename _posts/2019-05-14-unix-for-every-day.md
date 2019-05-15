---
published: true
---
   
### Find 

Find all files in the logs and remove it
`find . | grep logs | grep -e .zip | xargs rm`
 
Search all files from /root that contains the string "Linux", case insensitive:
`find  /root -type f -iname "*linux*"`
Search all directories from /root that contains the string "Linux", case insensitive:
`find  /root -type d -iname "*linux*"`

### Grep

Grep gz files
`find -iname "*.gz" -print0 | xargs -0 zgrep "321543314004027"`

`grep -rnw -e "fcd0d898-584d-11e7-a96b-0050568b7c54"`
Grep sock or ITEM
`grep -E "(sock|ITEM)"`
Grep process ttyv and exclude grep process from result
`ps -afx | grep ttyv | grep -v grep`

Show the bigest 20 files in the directory
`du -hsx * | sort -rh | head -20`
Show diskspace
`df -h` 

Отсортировать процессы по потреблению памяти
`ps aux --sort=%mem`
Запустить в бэкенде процем без логов
`nohup ./run-psdb.sh >/dev/null 2>&1 &`

Hot to clean file
- `truncate -s 0 filename`
- `>filename`

How to copy files by ssh
scp <source> <destination>

To copy a file from B to A while logged: 
- `scp username@b:/path/to/file /path/to/destination`
To copy a file from B to A while logged into B:
- `scp /path/to/file username@a:/path/to/destination`
