##### IOError: decoder jpeg not available

libjpeg-dev is required to be able to process jpegs with PIL, so you need to install it and then recompile PIL.

sudo apt-get install libjpeg-dev

On Ubuntu:

```

    install libjpeg-dev with apt sudo apt-get install libjpeg-dev 
    reinstall PIL pip install -I PIL 
```

If that doesn't work, try this:

sudo ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so /usr/lib 
sudo ln -s /usr/lib/x86_64-linux-gnu/libfreetype.so /usr/lib
sudo ln -s /usr/lib/x86_64-linux-gnu/libz.so /usr/lib 

reinstall PIL pip install -I PIL

```
    sudo pip install -I PIL
```

##### sudo apt-get install python-pygame

