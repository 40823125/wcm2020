---
Title: wcm2020(ssh)
Date: 2020-06-23 10:28
Category: Misc
Tags: 2020wcm
Slug: wcn2020-1
Author: yen
---

建立ssh

<!-- PELICAN_END_SUMMARY -->

<p><iframe allowfullscreen="allowfullscreen" height="314" src="//www.youtube.com/embed/BfReeoUSCHE" width="560"></iframe></p>
----

<p>1. 下載 Putty 工具組</p>
<p style="padding-left: 30px;"><span>從 </span><a href="https://www.chiark.greenend.org.uk/~sgtatham/putty/" rel="nofollow">https://www.chiark.greenend.org.uk/~sgtatham/putty/</a><span><span> </span>下載一般版, 或從<span> </span></span><a href="http://jakub.kotrla.net/putty/" rel="nofollow">http://jakub.kotrla.net/putty/</a><span><span> </span>下載特殊的可攜版本.</span></p>
<p><span>2. 利用 y:\portablegit\bin\sh.exe 進入 shell 命令環境後, 以 </span></p>
<pre class="brush:js;auto-links:false;toolbar:false" contenteditable="false"> ssh-keygen -t rsa -b 4096 -C "使用者學號"</pre>
<p style="padding-left: 30px;">在 /y/home/.ssh 目錄下建立 id_rsa 與 id_rsa.pub 等 private key 與 public key</p>
<p style="padding-left: 30px;">之後以 SciTE 開啟 id_rsa.pub 後, 將此 public key 的內容, 以新增添加到 Github.com 帳號下 personal settings -&gt; SSH and GPG keys 頁面下.</p>
<p>3. 接下來要利用 puttygen.exe 將 id_rsa 轉為 Putty 可以解讀的 .ppk 格式, 並修改隨身系統的啟動批次檔案, 指定利用 putty 目錄下的 plink 執行 git 指令的網路代理設定.</p>
<pre class="brush:js;auto-links:false;toolbar:false" contenteditable="false">修改啟動的 start.bat 加入下列設定:

set GIT_HOME=%Disk%:\portablegit\bin\
set GIT_SSH=%Disk%:\putty\plink.exe</pre>
<p>4. 利用 puttygen.exe 載入第二步驟所建立的 private key, 也就是 id_rsa.</p>
<p>開啟 puttygen 之後, 以右下方的 load 載入 id_rsa, 成功載入後, 利用 save private key 按鈕, 將已經轉為 putty 格式的 .ppk 存檔. 此一 .ppk 檔案必須在設定 putty 中 github.com session 時, 在 Connection-&gt;SSH-&gt;Auth 項目下, 將轉檔後的 .ppk 指向 private key file for authentication 欄位.</p>
<p>並在 Connection-&gt;Proxy 項目下, 指定 Proxy type: HTTP, 並將 IPv6 代理主機設為 ::53 或 ::42 埠號設為 3128.</p>
<p>5. 之後確定 home 下的 .ssh 目錄中的 config 設定檔案為:</p>
<pre class="brush:js;auto-links:false;toolbar:false" contenteditable="false"># no proxy at home
#ProxyCommand y:/PortableGit/mingw64/bin/connect.exe -H proxy.mde.nfu.edu.tw:3128 %h %p
# set git_ssh=y:/putty/plink.exe with auth under putty github.com session setup
ProxyCommand y:/putty/plink.exe github.com %h %p
 
Host github.com
    User git
    Port 22
    Hostname github.com
    
    # for connect.exe need openssh key format
    #IdentityFile "y:\home\.ssh\id_rsa_mdecourse"
    # for plink.exe need rsa key format but set under putty github.com session
    # plink.exe do not need the following setting
    #IdentityFile "y:\home\.ssh\mdecourse_putty_private.ppk"
 
    TCPKeepAlive yes
    IdentitiesOnly yes
</pre>
<p>6. 最後再將 wcmj2020 倉儲中 .git 目錄下的 config 檔案中的連線協定, 由 https 改為採 ssh 連線: 範例如下:</p>
<pre class="brush:js;auto-links:false;toolbar:false" contenteditable="false">[core]
	repositoryformatversion = 0
	filemode = false
	bare = false
	logallrefupdates = true
	symlinks = false
	ignorecase = true
[submodule]
	active = .
[remote "origin"]
	#url = https://github.com/mdecourse/wcmj2020.git
    url = git@github.com:mdecourse/wcmj2020.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
[submodule "cmsimde"]
	url = https://github.com/mdecourse/cmsimde.git</pre>
<p>之後就可以透過近端的 .ppk private key 與 Github.com 上的 public key 對應, 無需輸入帳號密碼就可以進行 git push.</p>

<!-- for LaTeX equations -->
<script src="https://40823125.github.io/web/math/MathJax.js?config=TeX-MML-AM_CHTML" type="text/javascript"></script>