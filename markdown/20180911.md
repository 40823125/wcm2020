---
Title: wcm2020(ubuntu)
Date: 2020-06-23 10:28
Category: Misc
Tags: 2020wcm
Slug: wcm2020-2
Author: yen
---
<p>用 Virtualbox 建立ubuntu</p>

<!-- PELICAN_END_SUMMARY -->

<p><iframe allowfullscreen="allowfullscreen" height="314" src="//www.youtube.com/embed/D7llxFAGAsw" width="560"></iframe><iframe allowfullscreen="allowfullscreen" height="314" src="//www.youtube.com/embed/yl_n4TmiatI" width="560"></iframe><iframe allowfullscreen="allowfullscreen" height="314" src="//www.youtube.com/embed/PzSosblmtxw" width="560"></iframe><iframe allowfullscreen="allowfullscreen" height="314" src="//www.youtube.com/embed/rUCiE53VSCY" width="560"></iframe></p>
----
<p><b>前面步驟為安裝設定重點為ipv4及ipv6網路設定都為自動</b><br/><b></b></p>
<p><b>進入介面後，再輸入指令</b></p>
<p><b>設定網域</b></p>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo vi 00-installer-config.yaml</pre>
<p><b></b> <strong>輸入指令</strong></p>
<p><strong>網路部分設定</strong></p>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo netplan apply</pre>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">ping4 140.130.15.254</pre>
<p><b></b><b>安裝pip3</b></p>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo apt install net-tools</pre>
<p></p>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo apt update</pre>
<p></p>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo apt install python3-pip</pre>
<p><b>利用pip3安裝flask flask_cors bs4 lxml markdown</b></p>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo pip3 install flask flask_cors bs4 lxml markdown</pre>
<p><strong>建立github資料夾</strong></p>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">mkdir github</pre>
<p><strong>安裝桌面</strong></p>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo apt install xorg</pre>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo apt install fluxbox</pre>
<pre class="brush:html;auto-links:false;toolbar:false" contenteditable="false">sudo apt install lxde</pre>
