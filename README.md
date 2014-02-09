GoagentConfig
=============

The usage and configuration about Goagent and google_appengine
# Offical webiste
- [Google Appengine](https://developers.google.com/appengine/)
    - [Google App Engine SDK for Python](https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python)
- [Goagent](http://www.goagent.org/)
    - [Download](https://code.google.com/p/goagent/downloads/list)

# Latest Version
## Install
- Download
    - [Google App Engine](https://developers.google.com/appengine/downloads)
        <pre><code>$ wget http://googleappengine.googlecode.com/files/google_appengine_1.8.9.zip</code></pre>
    - [Goagent](https://github.com/goagent/goagent)
        <pre><code>$ wget https://goagent.googlecode.com/files/goagent-2.1.5.7z</code></pre>

- Extract
<pre><code>$ unzip google_appengine_1.8.5.zip
$ 7zr e goagent-2.1.5.7z -ogoogle_appengine/goagent/
</code></pre>

## Configuration
- goagent/local/proxy.ini
    - appid = <YourID>
    - For example:
    <pre><code>[gae]
    appid = woainvzu
    </code></pre>
- goagent/server/python/app.yaml
    - application: <YourID>
    - For example:
    <pre><code>application: woainvzu
    </code></pre>
- Update configure
<pre><code>$ python appcfg.py update goagent/server/python/
</code></pre>

## Run Goagent
- Run in Terminal:
<pre><code>$ python <Path_to_GoogleAppEngine>/google_appengine/goagent/local/proxy.py
</code></pre>
- Run as command:
<pre><code>$ cat "python <Path_to_GoogleAppEngine>/google_appengine/goagent/local/proxy.py" > runProxy
$ chmod +x runProxy
$ sudo ln -s <PATH_TO_RUNPROXY>/runProxy /usr/bin/runProxy
$ runProxy
</code></pre>
- Or copy `Scripts/runProxy` to <SOME_PATH>
And use `ln -s`

# Older version
## How to install
1. Apply the account from **Google app engine** (https://appengine.google.com/)
2. Download the stable **goagent** from http://code.google.com/p/goagent/ and expand it
3. Download the stable **Google app engiene** from https://code.google.com/p/googleappengine/downloads/list and expand it
4. Copy <code>goagent</code> foler to <code>google_appengine</code> folder
    <pre><code>$ cp -r Goagent/ google_appengine/
    $ tree google_appengine/ -L 1
    google_appengine
    ������ api_server.py
    ������ appcfg.py
    ������ BUGS
    ������ bulkload_client.py
    ������ bulkloader.py
    ������ demos
    ������ dev_appserver.py
    ������ download_appstats.py
    ������ gen_protorpc.py
    ������ goagent
    ������ google
    ������ google_sql.py
    ������ lib
    ������ LICENSE
    ������ new_project_template
    ������ README
    ������ RELEASE_NOTES
    ������ remote_api_shell.py
    ������ tools
    ������ VERSION
    </code></pre>
5. Modify files:
    - **/google_appengine/goagent/local/proxy.ini:**
        - Format:
        <pre><code>[gae]
        appid = \<MyAppID\>
        ...
        </code></pre>
        - For Example:
        <pre><code>$ head proxy.ini
        [listen]
        ip = 127.0.0.1
        port = 8087
        visible = 1
        debuginfo = 0
        [gae]
        appid = woainvzu
        password =
        path = /2
        </code></pre>
    - **/google_appengine/goagent/server/python/app.yaml:**
        - Format:
        <pre><code>application: \<MyAppID\>
        </code></pre>
        - For Example:
        <pre><code>$ head app.yaml
        application: woainvzu
        version: 1
        runtime: python27
        api_version: 1
        threadsafe: true
        handlers:
        url: /fetch\.py
        script: wsgi_old.app
        secure: optional
        </code></pre>
6. Upload:
    - <pre><code>$ cd google_appengine
    $ sudo python appcfg.py update goagent/server/python
    </code></pre>
    - Input user account and password after if necessary
7. Configure the Firefox:
    - Download plugin **autoproxy** from https://addons.mozilla.org/en-us/firefox/addon/autoproxy/
    - Other confurations: http://www.i7086.com/gugeyingyonggoagentrangninziyoufangwenwangluotuwenjiaocheng
8. Run goagent:
    <pre><code>$ cd /google_appengine/goagent/local
    $ python proxy,py
    </code></pre>
9. Done


## ��ΰ�װ
�������: http://code.google.com/p/goagent/issues/detail?can=2&start=0&num=100&q=&colspec=ID%20Type%20Status%20Priority%20Milestone%20Owner%20Summary&groupby=&sort=&id=3473

1. ��https://appengine.google.com/ ����google app engine��appid
2. ����goagent�ȶ��� http://code.google.com/p/goagent/, ��ѹ�õ�goagent
3. ����google agent goagent ��linux�汾: http://googleappengine.googlecode.com/, ��ѹ�õ�google_appengine
4. ��goagent���Ƶ�google_appengine��
5. �޸��ļ���
    - **/google_appengine/goagent/local/proxy.ini:**
        - ��ʽ����appid��Ϊ�����appid
        <pre><code>[gae]
        appid = <�����AppID>
        </code></pre>
        - ��:
        <pre><code>$ head proxy.ini
        [listen]
        ip = 127.0.0.1
        port = 8087
        visible = 1
        debuginfo = 0
        [gae]
        appid = woainvzu
        password =
        path = /2
        </code></pre>
    - **/google_appengine/goagent/server/python/app.yaml:**
        - ��ʽ: ��application��Ϊ�����appid
        <pre><code>application: <�����AppID>
        </code></pre>
        - ��:
        <pre><code>$ head app.yaml
        application: woainvzu
        version: 1
        runtime: python27
        api_version: 1
        threadsafe: true
        handlers:
        url: /fetch\.py
        script: wsgi_old.app
        secure: optional
        </code></pre>
6. �ϴ�:
    - ��google_appengineĿ¼��ִ��
    <pre><code>$ cd google_appengine
    $ sudo python appcfg.py update goagent/server/python</code></pre>
    - ��ʾ������gmail�˻�������
7. Firefox����:
    - ���ز��: autoproxy ��https://addons.mozilla.org/en-us/firefox/addon/autoproxy/��
    - ��������: http://www.i7086.com/gugeyingyonggoagentrangninziyoufangwenwangluotuwenjiaocheng
8. ����goagent:
    <pre><code>$ cd /google_appengine/goagent/local
    $ python proxy,py
    </code></pre>
9. ���

# Q&A
1. ��������һ�ζ�����֤������
2. ��goagent/server/python/app.yaml�е�version��Ϊ2������version: 2
3. �޸ı�����DNSΪ8.8.8.8

ʹ��google_appengine��Ŀ���Ƿ�ֹgoagent��V�ϴ���ʱ��ײǽ������������ƺ�ʹ����google_appengine����Ҫײǽ���������ϴ���ʱ��������⣬������Ҫ��DNS��Ϊ8.8.8.8������google�ķ�����ip����ʲô�������š���
