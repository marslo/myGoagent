GoagentConfig
=============

The usage and configuration about Goagent and google_appengine
# Offical webiste
- [Google Appengine](https://developers.google.com/appengine/)
    - [Google App Engine SDK for Python](https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python)
- [Goagent](http://www.goagent.org/)
    - [Google Doc](https://code.google.com/p/goagent/downloads/list)
    - [Github](https://github.com/goagent/goagent)

## Download and Installation
- Download

      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ wget https://storage.googleapis.com/appengine-sdks/featured/google_appengine_1.9.6.zip
      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ wget https://nodeload.github.com/goagent/goagent/legacy.zip/3.0
    

- Extract

      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ unzip google_appengine_1.9.6.zip
      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ unzip goagent-goagent-v3.1.18-27-g0772f4e.zip

## Configuration for Latest version (goagent v3.1.18)
- Details can all be found at [Goagent Wiki](https://code.google.com/p/goagent/wiki/GoAgent_Linux); If the official wiki cannot be opened, Details as below

### Environment Dependences installation
- The commands

      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ sudo apt-get install python-dev python-greenlet python-gevent python-vte python-openssl python-crypto python-appindicator

- Mandatory selections
    - Python 2 (2.7 is recommend)
    - gevent 1.0: for multithreaded
    - greenlet: dependence of gevent
    - python-vte: The GUI lib based on GTK
    - python-openssl 0.13: For generate CA.crt
    - pycrypto: For RC4 crypto
    - python-appindicator: The indicator stuff in Unity

### Gevent installation:
- Installation by automatic
    
      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ sudo apt-get install python-dev python-pip && sudo pip install gevent --upgrade
- Installation by manually
    - For gevent 0.4.x
    
          ┌─ (marslo@MarsloJiao ~) ->
          └─ $ wget http://mirrors.aliyun.com/pypi/packages/source/g/greenlet/greenlet-0.4.2.zip && unzip greenlet-0.4.2.zip && cd greenlet-0.4.2 && sudo python setup.py install

    - For gevent 1.x
    
          ┌─ (marslo@MarsloJiao ~) ->
          └─ $ wget http://mirrors.aliyun.com/pypi/packages/source/g/gevent/gevent-1.0.tar.gz && tar xvzpf gevent-1.0.tar.gz && cd gevent-1.0 && sudo python setup.py install


### Configuration
- Copy/Move `goagent` folder to `google_appengine`
    
      ┌─ (marslo@MJ ~/Tools/Software/Applications/Proxy) ->
      └─ $ mv goagent/ google_appengine/
- Edit `goagent/local/proxy.ini`
    - appid = <YourID>
    - For example:
        
        [gae]
        appid = woainvzu-9

- Edit `goagent/server/python/app.yaml`
    - application: <YourID>
    - For example:
        
        application: woainvzu-9
        
- Update configure (By using google_appengine)
    
      $ python appcfg.py update goagent/server/gae/
    
### Upload and Run
- Upload
    
      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ python [GOAGENT_PATH]/server/uploader.zip

- Run goagent
    
      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ python [GOAGENT_PATH]/local/proxy.py
      OR
      ┌─ (marslo@MarsloJiao ~) ->
      └─ $ python [GOAGENT_PATH]/local/goagent-gtk.py

## _Configuration for older Goagent version_

- <i>goagent/local/proxy.ini
    
      ...
      [gae]
      appid = woainvzu
      ...

- <i>goagent/server/python/app.yaml
    
      application: woainvzu
      ...
        
- <i>Update configure
    
      $ python appcfg.py update goagent/server/python/

## Run Goagent
- Run in Terminal:

      $ python <Path_to_GoogleAppEngine>/google_appengine/goagent/local/proxy.py


- Run as command:

      $ cat "python <Path_to_GoogleAppEngine>/google_appengine/goagent/local/proxy.py" > runProxy
      $ chmod +x runProxy
      $ sudo ln -s <PATH_TO_RUNPROXY>/runProxy /usr/bin/runProxy
      $ runProxy

- Or copy `Scripts/runProxy` to <SOME_PATH>
And use `ln -s`

# Older version
## How to install
1. Apply the account from **Google app engine** (https://appengine.google.com/)
2. Download the stable **goagent** from http://code.google.com/p/goagent/ and expand it
3. Download the stable **Google app engiene** from https://code.google.com/p/googleappengine/downloads/list and expand it
4. Copy <code>goagent</code> foler to <code>google_appengine</code> folder
    
       $ cp -r Goagent/ google_appengine/
       $ tree google_appengine/ -L 1
       google_appengine
       ├── api_server.py
       ├── appcfg.py
       ├── BUGS
       ├── bulkload_client.py
       ├── bulkloader.py
       ├── demos
       ├── dev_appserver.py
       ├── download_appstats.py
       ├── gen_protorpc.py
       ├── goagent
       ├── google
       ├── google_sql.py
       ├── lib
       ├── LICENSE
       ├── new_project_template
       ── README
       ├── RELEASE_NOTES
       ├── remote_api_shell.py
       ├── tools
       └── VERSION
    
5. Modify files:
    - **/google_appengine/goagent/local/proxy.ini:**
        - Format:
        
              [gae]
              appid = \<MyAppID\>
              ...

        - For Example:
        
              $ head proxy.ini
              [listen]
              ip = 127.0.0.1
              port = 8087
              visible = 1
              debuginfo = 0
              [gae]
              appid = woainvzu
              password =
              path = /2


    - **/google_appengine/goagent/server/python/app.yaml:**
        - Format:
        
              application: \<MyAppID\>

        - For Example:
        
              $ head app.yaml
              application: woainvzu
              version: 1
              runtime: python27
              api_version: 1
              threadsafe: true
              handlers:
              url: /fetch\.py
              script: wsgi_old.app
              secure: optional

6. Upload:
    
       $ cd google_appengine
       $ sudo python appcfg.py update goagent/server/python

    - Input user account and password after if necessary
7. Configure the Firefox:
    - Download plugin **autoproxy** from https://addons.mozilla.org/en-us/firefox/addon/autoproxy/
    - Other confurations: http://www.i7086.com/gugeyingyonggoagentrangninziyoufangwenwangluotuwenjiaocheng
8. Run goagent:
    
       $ cd /google_appengine/goagent/local
       $ python proxy,py
       
9. Done

## 如何安装
详情参照: http://code.google.com/p/goagent/issues/detail?can=2&start=0&num=100&q=&colspec=ID%20Type%20Status%20Priority%20Milestone%20Owner%20Summary&groupby=&sort=&id=3473

1. 在https://appengine.google.com/ 申请google app engine的appid
2. 下载goagent稳定版 http://code.google.com/p/goagent/, 解压得到goagent
3. 下载google agent goagent 的linux版本: http://googleappengine.googlecode.com/, 解压得到google_appengine
4. 将goagent复制到google_appengine中
5. 修改文件：
    - **/google_appengine/goagent/local/proxy.ini:**
        - 格式：将appid改为申请的appid
        
              [gae]
              appid = <申请的AppID>

         - 例:
        
               $ head proxy.ini
               [listen]
               ip = 127.0.0.1
               port = 8087
               visible = 1
               debuginfo = 0
               [gae]
               appid = woainvzu
               password =
               path = /2

    - **/google_appengine/goagent/server/python/app.yaml:**
        - 格式: 将application改为申请的appid
        
              application: <申请的AppID>
        
        - 例:
        
              $ head app.yaml
              application: woainvzu
              version: 1
              runtime: python27
              api_version: 1
              threadsafe: true
              handlers:
              url: /fetch\.py
              script: wsgi_old.app
              secure: optional

6. 上传:
    - 在google_appengine目录下执行
    
          $ cd google_appengine
          $ sudo python appcfg.py update goagent/server/python
        
    - 提示后输入gmail账户和密码
7. Firefox设置:
    - 下载插件: autoproxy （https://addons.mozilla.org/en-us/firefox/addon/autoproxy/）
    - 具体设置: http://www.i7086.com/gugeyingyonggoagentrangninziyoufangwenwangluotuwenjiaocheng
8. 运行goagent:
        
       $ cd /google_appengine/goagent/local
       $ python proxy,py
   
9. 完成

# Q&A
1. 重新生成一次二次验证的密码
2. 将goagent/server/python/app.yaml中的version设为2，即：version: 2
3. 修改本机的DNS为8.8.8.8

使用google_appengine的目的是防止goagent在V上传的时候撞墙。。但是最近似乎使用了google_appengine还是要撞墙，所以在上传的时候出现问题，所以需要将DNS设为8.8.8.8，这是google的服务器ip还是什么东西来着。。
