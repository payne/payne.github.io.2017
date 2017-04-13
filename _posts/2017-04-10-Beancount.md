---
layout: post
title: "Beancount -- Double Entry Accounting"
categories: budget accounting
---

I think [http://ledger-cli.org/](http://ledger-cli.org/) was the first open source, command line & text based double entry accounting system.

There are a bunch of 
https://github.com/ledger/ledger/wiki/Ports

https://goo.gl/0BpOhu is "The Double-Entry Couting Method" and helped me the most in understanding.  


I really like c9.io.   The private virtual machine where I write this blog runs Ubuntu 14.04.   

I wanted to setup a custom python3 environment to run beancount.  So I started by installing virtualenv:

```
payne:~ $ sudo pip3 install virtualenv                                                                                                                                  
Downloading/unpacking virtualenv
  Downloading virtualenv-15.1.0-py2.py3-none-any.whl (1.8MB): 1.8MB downloaded
Installing collected packages: virtualenv
Successfully installed virtualenv
Cleaning up...
payne:~ $ 
```




payne:~ $ mkdir myPython3
payne:~ $ cd myPython3
payne:~/myPython3 $ virtualenv .
Using base prefix '/usr'
New python executable in /home/ubuntu/myPython3/bin/python3
Also creating executable in /home/ubuntu/myPython3/bin/python
Installing setuptools, pip, wheel...done.
payne:~/myPython3 $ 

http://python-guide-pt-br.readthedocs.io/en/latest/dev/virtualenvs/


./configure --prefix=/home/ubuntu/local

payne:~/local/bin $ export PATH=`pwd`:${PATH}

payne:~ $ which pip3
/home/ubuntu/local/bin/pip3
payne:~ $ pip3 install virtualenv
Collecting virtualenv
  Downloading virtualenv-15.1.0-py2.py3-none-any.whl (1.8MB)
    100% |████████████████████████████████| 1.8MB 580kB/s 
Installing collected packages: virtualenv
Successfully installed virtualenv-15.1.0
payne:~ $ history | grep configure


payne:~ $ mkdir myPython3
payne:~ $ cd myPython3
payne:~/myPython3 $ virtualenv .
Using base prefix '/home/ubuntu/local'
New python executable in /home/ubuntu/myPython3/bin/python3.6
Also creating executable in /home/ubuntu/myPython3/bin/python
Installing setuptools, pip, wheel...done.
payne:~/myPython3 $ virtualenv --relocatable .
Making script /home/ubuntu/myPython3/bin/python-config relative
Making script /home/ubuntu/myPython3/bin/wheel relative
Making script /home/ubuntu/myPython3/bin/pip3 relative
Making script /home/ubuntu/myPython3/bin/pip3.6 relative
Making script /home/ubuntu/myPython3/bin/pip relative
Making script /home/ubuntu/myPython3/bin/easy_install-3.6 relative
Making script /home/ubuntu/myPython3/bin/easy_install relative
payne:~/myPython3 $ 


(myPython3) payne:~/myPython3 $ pip3 install beancount
Collecting beancount
  Downloading beancount-2.0b15.tar.gz (554kB)
    100% |████████████████████████████████| 563kB 1.8MB/s 
Collecting python-dateutil (from beancount)
  Downloading python_dateutil-2.6.0-py2.py3-none-any.whl (194kB)
    100% |████████████████████████████████| 194kB 3.6MB/s 
Collecting ply (from beancount)
  Downloading ply-3.10.tar.gz (150kB)
    100% |████████████████████████████████| 153kB 4.5MB/s 
Collecting bottle (from beancount)
  Downloading bottle-0.12.13.tar.gz (70kB)
    100% |████████████████████████████████| 71kB 5.2MB/s 
Collecting lxml (from beancount)
  Downloading lxml-3.7.3-cp36-cp36m-manylinux1_x86_64.whl (7.2MB)
    100% |████████████████████████████████| 7.2MB 200kB/s 
Collecting python-magic (from beancount)
  Downloading python_magic-0.4.13-py2.py3-none-any.whl
Collecting beautifulsoup4 (from beancount)
  Downloading beautifulsoup4-4.5.3-py3-none-any.whl (85kB)
    100% |████████████████████████████████| 92kB 7.2MB/s 
Collecting chardet (from beancount)
  Downloading chardet-2.3.0-py2.py3-none-any.whl (180kB)
    100% |████████████████████████████████| 184kB 5.8MB/s 
Collecting google-api-python-client (from beancount)
  Downloading google_api_python_client-1.6.2-py2.py3-none-any.whl (52kB)
    100% |████████████████████████████████| 61kB 10.0MB/s 
Requirement already satisfied: six>=1.5 in ./lib/python3.6/site-packages (from python-dateutil->beancount)
Collecting uritemplate<4dev,>=3.0.0 (from google-api-python-client->beancount)
  Downloading uritemplate-3.0.0-py2.py3-none-any.whl
Collecting oauth2client<5.0.0dev,>=1.5.0 (from google-api-python-client->beancount)
  Downloading oauth2client-4.0.0-py2.py3-none-any.whl (184kB)
    100% |████████████████████████████████| 194kB 4.8MB/s 
Collecting httplib2<1dev,>=0.9.2 (from google-api-python-client->beancount)
  Downloading httplib2-0.10.3.tar.gz (204kB)
    100% |████████████████████████████████| 204kB 3.7MB/s 
Collecting pyasn1-modules>=0.0.5 (from oauth2client<5.0.0dev,>=1.5.0->google-api-python-client->beancount)
  Downloading pyasn1_modules-0.0.8-py2.py3-none-any.whl
Collecting rsa>=3.1.4 (from oauth2client<5.0.0dev,>=1.5.0->google-api-python-client->beancount)
  Downloading rsa-3.4.2-py2.py3-none-any.whl (46kB)
    100% |████████████████████████████████| 51kB 7.3MB/s 
Collecting pyasn1>=0.1.7 (from oauth2client<5.0.0dev,>=1.5.0->google-api-python-client->beancount)
  Downloading pyasn1-0.2.3-py2.py3-none-any.whl (53kB)
    100% |████████████████████████████████| 61kB 10.2MB/s 
Building wheels for collected packages: beancount, ply, bottle, httplib2
  Running setup.py bdist_wheel for beancount ... done
  Stored in directory: /home/ubuntu/.cache/pip/wheels/a3/4e/5f/3f7f386c5376387b80da65b5895d6b28869c451e612aced32c
  Running setup.py bdist_wheel for ply ... done
  Stored in directory: /home/ubuntu/.cache/pip/wheels/ad/dd/ad/8ce1991a7b380dfe23d6cc81a4de5c2775bc728b5a0a7721aa
  Running setup.py bdist_wheel for bottle ... done
  Stored in directory: /home/ubuntu/.cache/pip/wheels/49/cf/37/132916b926fae01d6e27d94c0018e3ad07452ec3760e24a36a
  Running setup.py bdist_wheel for httplib2 ... done
  Stored in directory: /home/ubuntu/.cache/pip/wheels/ca/ac/5f/749651f7925b231103f5316cacca82a487810c22d30f011c0c
Successfully built beancount ply bottle httplib2
Installing collected packages: python-dateutil, ply, bottle, lxml, python-magic, beautifulsoup4, chardet, uritemplate, pyasn1, pyasn1-modules, rsa, httplib2, oauth2client, google-api-python-client, beancount
Successfully installed beancount-2.0b15 beautifulsoup4-4.5.3 bottle-0.12.13 chardet-2.3.0 google-api-python-client-1.6.2 httplib2-0.10.3 lxml-3.7.3 oauth2client-4.0.0 ply-3.10 pyasn1-0.2.3 pyasn1-modules-0.0.8 python-dateutil-2.6.0 python-magic-0.4.13 rsa-3.4.2 uritemplate-3.0.0
(myPython3) payne:~/myPython3 $ 
(myPython3) payne:~/myPython3 $ 






(myPython3) payne:~/myPython3 $ 
(myPython3) payne:~/myPython3 $ cd
(myPython3) payne:~ $ pip install fava
Collecting fava
  Downloading fava-1.3-py3-none-any.whl (554kB)
    100% |████████████████████████████████| 563kB 1.7MB/s 
Collecting Flask>=0.10.1 (from fava)
  Downloading Flask-0.12.1-py2.py3-none-any.whl (82kB)
    100% |████████████████████████████████| 92kB 4.3MB/s 
Collecting click (from fava)
  Downloading click-6.7-py2.py3-none-any.whl (71kB)
    100% |████████████████████████████████| 71kB 5.7MB/s 
Collecting markdown2>=2.3.0 (from fava)
  Downloading markdown2-2.3.3.zip (156kB)
    100% |████████████████████████████████| 163kB 4.3MB/s 
Collecting Flask-Babel>=0.10.0 (from fava)
  Downloading Flask-Babel-0.11.1.tar.gz (40kB)
    100% |████████████████████████████████| 40kB 6.3MB/s 
Requirement already satisfied: beancount>=2.0b15 in ./myPython3/lib/python3.6/site-packages (from fava)
Collecting itsdangerous>=0.21 (from Flask>=0.10.1->fava)
  Downloading itsdangerous-0.24.tar.gz (46kB)
    100% |████████████████████████████████| 51kB 7.8MB/s 
Collecting Jinja2>=2.4 (from Flask>=0.10.1->fava)
  Downloading Jinja2-2.9.6-py2.py3-none-any.whl (340kB)
    100% |████████████████████████████████| 348kB 4.3MB/s 
Collecting Werkzeug>=0.7 (from Flask>=0.10.1->fava)
  Downloading Werkzeug-0.12.1-py2.py3-none-any.whl (312kB)
    100% |████████████████████████████████| 317kB 3.0MB/s 
Collecting Babel>=2.3 (from Flask-Babel>=0.10.0->fava)
  Downloading Babel-2.4.0-py2.py3-none-any.whl (6.8MB)
    100% |████████████████████████████████| 6.8MB 195kB/s 
Requirement already satisfied: lxml in ./myPython3/lib/python3.6/site-packages (from beancount>=2.0b15->fava)
Requirement already satisfied: python-dateutil in ./myPython3/lib/python3.6/site-packages (from beancount>=2.0b15->fava)
Requirement already satisfied: beautifulsoup4 in ./myPython3/lib/python3.6/site-packages (from beancount>=2.0b15->fava)
Requirement already satisfied: bottle in ./myPython3/lib/python3.6/site-packages (from beancount>=2.0b15->fava)
Requirement already satisfied: python-magic in ./myPython3/lib/python3.6/site-packages (from beancount>=2.0b15->fava)
Requirement already satisfied: google-api-python-client in ./myPython3/lib/python3.6/site-packages (from beancount>=2.0b15->fava)
Requirement already satisfied: chardet in ./myPython3/lib/python3.6/site-packages (from beancount>=2.0b15->fava)
Requirement already satisfied: ply in ./myPython3/lib/python3.6/site-packages (from beancount>=2.0b15->fava)
Collecting MarkupSafe>=0.23 (from Jinja2>=2.4->Flask>=0.10.1->fava)
  Downloading MarkupSafe-1.0.tar.gz
Collecting pytz>=0a (from Babel>=2.3->Flask-Babel>=0.10.0->fava)
  Downloading pytz-2017.2-py2.py3-none-any.whl (484kB)
    100% |████████████████████████████████| 491kB 2.2MB/s 
Requirement already satisfied: six>=1.5 in ./myPython3/lib/python3.6/site-packages (from python-dateutil->beancount>=2.0b15->fava)
Requirement already satisfied: oauth2client<5.0.0dev,>=1.5.0 in ./myPython3/lib/python3.6/site-packages (from google-api-python-client->beancount>=2.0b15->fava)
Requirement already satisfied: uritemplate<4dev,>=3.0.0 in ./myPython3/lib/python3.6/site-packages (from google-api-python-client->beancount>=2.0b15->fava)
Requirement already satisfied: httplib2<1dev,>=0.9.2 in ./myPython3/lib/python3.6/site-packages (from google-api-python-client->beancount>=2.0b15->fava)
Requirement already satisfied: rsa>=3.1.4 in ./myPython3/lib/python3.6/site-packages (from oauth2client<5.0.0dev,>=1.5.0->google-api-python-client->beancount>=2.0b15->fava)
Requirement already satisfied: pyasn1-modules>=0.0.5 in ./myPython3/lib/python3.6/site-packages (from oauth2client<5.0.0dev,>=1.5.0->google-api-python-client->beancount>=2.0b15->fava)
Requirement already satisfied: pyasn1>=0.1.7 in ./myPython3/lib/python3.6/site-packages (from oauth2client<5.0.0dev,>=1.5.0->google-api-python-client->beancount>=2.0b15->fava)
Building wheels for collected packages: markdown2, Flask-Babel, itsdangerous, MarkupSafe
  Running setup.py bdist_wheel for markdown2 ... done
  Stored in directory: /home/ubuntu/.cache/pip/wheels/b7/14/0a/812d405dd929b40c8f18ed30159ddf9ce37d74154433dd54d6
  Running setup.py bdist_wheel for Flask-Babel ... done
  Stored in directory: /home/ubuntu/.cache/pip/wheels/99/65/6c/927249178edfdc24c9cb2d9fcea27f598a73b323a1b5e3a8fc
  Running setup.py bdist_wheel for itsdangerous ... done
  Stored in directory: /home/ubuntu/.cache/pip/wheels/fc/a8/66/24d655233c757e178d45dea2de22a04c6d92766abfb741129a
  Running setup.py bdist_wheel for MarkupSafe ... done
  Stored in directory: /home/ubuntu/.cache/pip/wheels/88/a7/30/e39a54a87bcbe25308fa3ca64e8ddc75d9b3e5afa21ee32d57
Successfully built markdown2 Flask-Babel itsdangerous MarkupSafe
Installing collected packages: itsdangerous, MarkupSafe, Jinja2, click, Werkzeug, Flask, markdown2, pytz, Babel, Flask-Babel, fava
Successfully installed Babel-2.4.0 Flask-0.12.1 Flask-Babel-0.11.1 Jinja2-2.9.6 MarkupSafe-1.0 Werkzeug-0.12.1 click-6.7 fava-1.3 itsdangerous-0.24 markdown2-2.3.3 pytz-2017.2
(myPython3) payne:~ $ 



fava -p ${PORT} -H ${IP} matt.beancount

