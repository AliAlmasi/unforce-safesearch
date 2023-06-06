<h1>Unforce Google SafeSearch</h1>
<p>Recently, the Iranian government <a href="https://digiato-com.translate.goog/article/2022/07/12/safesearch-internet-mobile?_x_tr_sl=fa&_x_tr_tl=en&_x_tr_hl=en&_x_tr_pto=wapp">has made changes</a> in the national DNS servers, which causes all DNS requests for Google to be sent to the domain <code>forcesafesearch.google.com</code> (to IP <code>216.239.38.120</code>), which forces all Google users,  regardless of their settings ,  have to use Google with the SafeSearch on.</p>
<h2>How to bypass this?</h2>
<p>To bypass this, the system must manually introduce Google's regular search servers (<code>google.com </code> - <code> 142.250.180.142</code>). For this, it is necessary to use the <code>hosts</code> file available in the operating systems to introduce the IP directly to the system so that it does not request Google's safe search from the country's DNS.</p>
<blockquote>Notice: This solution only works in Windows, macOS and Linux.</blockquote>
<h2>For Windows users</h2>
<p>On Windows, you need to open the Run window (<i>WinKey + R</i>) and type this as administrator:</p>
<pre>notepad C:\Windows\System32\Drivers\etc\hosts</pre>
<p>This will open the <code>hosts</code> file of your Windows on a Notepad.</p>
<p>Next, you need to add these lines at end of the file:</p>
<pre>142.250.180.142 google.com
142.250.180.142 www.google.com</pre>
<p>Save the file afterwards, open cmd and flush DNS cache by running <pre>ipconfig /flushdns</pre></p>
<p>Now you're all done. Check if it's working by opening <a href="https://google.com">google.com</a>, or run <code>nslookup google.com</code> on cmd and see what IP it returns.</p>
<h2>For macOS users</h2>
<p>Open Terminal and run <pre>sudo nano /private/etc/hosts</pre></p>
<p>Since we use sudo to edit the hosts file, you will be asked to enter the administrator password of your macOS user account. Type your admin password and hit the Enter key.
</p>
<blockquote>Note: The cursor doesn’t work in the command line. You'll need to use the arrow keys to navigate between the lines inside the hosts file.</blockquote>
<p>Paste these lines at the end of the file:</p>
<pre>142.250.180.142 google.com
142.250.180.142 www.google.com</pre>
<p>After that, press <i>CTRL + X</i> on your keyboard. Enter Y to save the changes, and hit the Enter button.</p>
<p>Then, you'll need to flush the DNS cache. to do this, if you're using macOS Monterey or Big Sur, run this: <pre>sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder</pre>Else, if you're using macOS Catalina, Mojave, High Sierra, Sierra, Mountain Lion or Lion, run this: <pre>sudo killall -HUP mDNSResponder</pre></p>
<p>Now you're all done. Check if it's working by opening <a href="https://google.com">google.com</a>, or run <code>nslookup google.com</code> on your Terminal and see what IP it returns.</p>
<h2>For Linux users</h2>
<p>Open Terminal and run this:<pre>sudo nano/etc/hosts</pre>Enter the password for sudo when asked.</p>
<p>Paste these lines at the end of the file:</p>
<pre>142.250.180.142 google.com
142.250.180.142 www.google.com</pre>
<p>After that, press <i>CTRL + X</i> on your keyboard. Enter Y to save the changes, and hit the Enter button.</p>
<p>Then, to flush the DNS cache on Linux, if you are using <code>systemd-resolved</code>, you can use the the command followed by <code>--flush-caches</code>.<br>Alternatively, you can use the <code>resolvectl</code> command followed by the <code>flush-caches</code> option.</p>
<pre>sudo systemd-resolve --flush-caches
sudo resolvectl flush-caches</pre>
<p>Now you're all done. Check if it's working by opening <a href="https://google.com">google.com</a>, or run <code>nslookup google.com</code> on your Terminal and see what IP it returns.</p>
