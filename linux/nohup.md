##### nohup

nohup python upload_queue.py>upload.log 2>&1 &

这个命令会把标准输出(print)重定向到upload.log文件，但是如果用logging 的话就不行(也许这个不算是个标准输出？),python  
会把标准输出写道buffer中，如果buffer不满的不会写入，如果想让每次输出都写入到文件使用sys.stdout.flush()输出buffer


##### jobs

查看nohup 任务
