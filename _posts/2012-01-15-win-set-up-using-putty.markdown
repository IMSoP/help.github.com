---
layout: default
title: Set Up Git Using PuTTY
description: An alternative guide to getting started with Git using the PuTTY family of tools
---

<p class="intro">If you&rsquo;ve found yourself on this page, we&rsquo;re assuming you&rsquo;re brand new to Git and GitHub. This guide will walk you through the basics and explain a little bit about how everything works along the way.</p>

<p class="intro">This is the guide for setting up git in <strong>Windows</strong> using the PuTTY family of tools (including Puttygen, Pageant, and Plink). The <strong><a href="/win-set-up-git">official guide for Windows set up</a></strong> uses "openssh"; there are also guides for <strong><a href="/mac-set-up-git">OSX</a></strong> and <strong><a href="/linux-set-up-git">Linux</a></strong>.</p>

##<span class="step">First:</span> Download and Install PuTTY and Git

SSH is used to establish a secure connection between your computer and GitHub. The most common set of tools for working with SSH on Windows is known as "PuTTY". You may already have some or all of these tools installed, but if you do not have the complete set, you will need to install them before you begin.

At the heart of GitHub is an open source version control system (VCS) called Git&#42;. Created by the same dudes that created Linux, Git is responsible for everything GitHub related that happens locally on your computer.

_&#42;If you don&rsquo;t already know what Git is, <a href="http://progit.org/book/ch1-3.html" target="_blank">take a crash course.</a>_

<ol>
  <li>
    <p><span class="step-title">Download and install the latest version of <a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html">the PuTTY family of tools</a>.</span></p>
    
    <p>Download the file listed as "A Windows installer for everything except PuTTYtel" and use the default options for each step.</p>
    
    <img src="/images/bootcamp/bootcamp_1_putty_install_1.jpg" width="558" height="442" alt="Welcome page" />
    <img src="/images/bootcamp/bootcamp_1_putty_install_2.jpg" width="558" height="442" alt="Select destination location" />
    <img src="/images/bootcamp/bootcamp_1_putty_install_3.jpg" width="558" height="442" alt="Select start menu folder" />
    <img src="/images/bootcamp/bootcamp_1_putty_install_4.jpg" width="558" height="442" alt="Additional icons and file associations" />
    <img src="/images/bootcamp/bootcamp_1_putty_install_5.jpg" width="558" height="442" alt="Summary" />
    <img src="/images/bootcamp/bootcamp_1_putty_install_6.jpg" width="558" height="442" alt="Installation complete" />
  </li>
  <li>
    <p><span class="step-title">Download and install the latest version of <a href="http://code.google.com/p/msysgit/downloads/list" target="_blank">Git for Windows</a>.</span></p>

    <p>Use the default options for each step, but when offered, select "Use (Tortoise)Plink", and enter "C:\Program Files\PuTTY\plink.exe" in the box provided.</p>

    <img src="/images/bootcamp/bootcamp_1_win_install_1.jpg" width="503" height="388" alt="Welcome page" />
    <img src="/images/bootcamp/bootcamp_1_win_install_2.jpg" width="503" height="388" alt="Information" />
    <img src="/images/bootcamp/bootcamp_1_win_install_3.jpg" width="503" height="388" alt="Select destination location" />
    <img src="/images/bootcamp/bootcamp_1_win_install_4.jpg" width="503" height="388" alt="Select start menu folder" />
    <img src="/images/bootcamp/bootcamp_1_win_install_5.jpg" width="503" height="388" alt="Select components" />
    <img src="/images/bootcamp/bootcamp_1_win_install_6.jpg" width="503" height="388" alt="Adjusting your PATH environment" />
    <img src="/images/bootcamp/bootcamp_1_win_install_6a.jpg" width="503" height="388" alt="Choosing the SSH executable" />
    <img src="/images/bootcamp/bootcamp_1_win_install_7.jpg" width="503" height="388" alt="Configuring the line ending conversions" />
    <img src="/images/bootcamp/bootcamp_1_win_install_8.jpg" width="503" height="388" alt="Installing" />
    <img src="/images/bootcamp/bootcamp_1_win_install_9.jpg" width="503" height="388" alt="Installation complete" />
  </li>
</ol>

##<span class="step">Next:</span> Set Up SSH Keys

We use SSH keys to establish a secure connection between your computer and GitHub. Setting them up is fairly easy, but does involve a number of steps.

1. <span class="step-title">Generate a new SSH key.</span> <span>Have an existing key pair? You can skip to Step 4.</span></span>

	To generate a new key pair, you will need to use the "PuTTYgen" utility installed with PuTTY. If you used the installer as above, you should have a shortcut to this in the "PuTTY" folder of your Start Menu.
	
	<img src="/images/bootcamp/bootcamp_1_puttygen_1.jpg" width="483" height="467" alt="PuTTY Key Generator main screen" />
	
	Click "Generate", and move your mouse back and forth across the empty area (the exact movements you make are more unpredictable than the computer alone, so create a more unpredictable key).
	
	<img src="/images/bootcamp/bootcamp_1_puttygen_2.jpg" width="483" height="467" alt="Generating randomness" />
	
	You should then see information about your newly generated key.
	
	<img src="/images/bootcamp/bootcamp_1_puttygen_3.jpg" width="483" height="467" alt="Key generated" />
	
	Now you need to enter a passphrase. (You may also want to change the "Key comment"; this is just a label that programs will you when you use the key.)
	
	<div class="more-info">
		<h4 class="compressed">Why do passphrases matter?</h4>
		<div class="more-content">
			<p>Passwords aren&rsquo;t very secure, you already know this. If you use one that&rsquo;s easy to remember, it&rsquo;s easier to guess or brute-force (try many options until one works). If you use one that&rsquo;s random it&rsquo;s hard to remember, and thus you&rsquo;re more inclined to write the password down. Both of these are Very Bad Things&trade;. This is why you&rsquo;re using ssh keys.</p>

			<p>But using a key without a passphrase is basically the same as writing down that random password in a file on your computer. Anyone who gains access to your drive has gained access to every system you use that key with. This is also a Very Bad Thing&trade;. The solution is obvious: add a passphrase.</p>

			<p><em>But I don&rsquo;t want to enter a long passphrase every time I use the key!</em></p>

			<p>Neither do we! Thankfully, there&rsquo;s a nifty little tool called <code>pageant</code> that can save your passphrase securely so you don&rsquo;t have to re-enter it.</p>

			<p>For more information about SSH key passphrases, check out our <a href="/working-with-key-passphrases">help guide</a>.</p>
		</div>
	</div>
	
	<img src="/images/bootcamp/bootcamp_1_puttygen_4.jpg" width="483" height="467" alt="Passphrase and key comment" />
	
	Finally, save your public and private keys for later use. It doesn't matter where you put them, but you'll need to be able to find them later in order to add them to Pageant.

	<img src="/images/bootcamp/bootcamp_1_puttygen_5.jpg" width="483" height="467" alt="Save public and private keys" />
	
2. <span class="step-title">Add your SSH key to GitHub.</span>

	Before you close PuTTYkeygen, you'll need to copy the public SSH key so that you can tell GitHub to trust it. Select and copy the text in the box labelled "Public key for pasting into OpenSSH authorized_keys file". (Note that this isn't quite the same format as the ".ppk" file you just saved. You can always ask PuTTYgen to open or import keys if you need to convert them from one format to the other.) <span class="attention">It&rsquo;s important you copy your SSH key exactly as it is written without adding any newlines or whitespace.</span>
	
	<img src="/images/bootcamp/bootcamp_1_puttygen_6.jpg" width="483" height="467" alt="Copying the public key in OpenSSH format" />

	On the GitHub site _Click &ldquo;Account Settings&rdquo;_ &gt; _Click &ldquo;SSH Public Keys&rdquo;_ &gt; _Click &ldquo;Add another public key&rdquo;_

	Now paste it into the &ldquo;Key&rdquo; field.

	<img src="/images/bootcamp/bootcamp_1_ssh.jpg" width="558" height="402" alt="Paste your SSH Key" />

	Hit &ldquo;Add Key.&rdquo;
	
3. <span class="step-title">Running Pageant.</span>

	In order for Putty to use your new key, you need to be running an "SSH Agent" named "Pageant", and to tell Pageant where your key is. You can do this in one click by creating a shortcut in your Start Menu.
	
	Right-click on the shortcut for Pageant in the PuTTY folder of your Start Menu, and select "Properties".
	
	<img src="/images/bootcamp/bootcamp_1_pageant_1.jpg" width="377" height="533" alt="Properties for default Pageant shortcut" />
	
	At the end of the "Target" box (leaving the existing text alone) add the path to the <strong>private</strong> key file you just generated. You can add multiple keys here, and they will be loaded by Pageant in turn.
	
	<img src="/images/bootcamp/bootcamp_1_pageant_2.jpg" width="377" height="533" alt="Target including path to private .ppk file" />
	
	Click OK. Now click on the shortcut you just edited; Pageant should start up, load your private key, and ask you for your passphrase:
	
	<img src="/images/bootcamp/bootcamp_1_pageant_3.jpg" width="216" height="126" alt="Pageant prompting for a passphrase" />
	
	Once running, Pageant will sit unobtrusively in the "notification area" ("system tray") next to the clock on the taskbar.
	
	<img src="/images/bootcamp/bootcamp_1_pageant_4.jpg" width="404" height="56" alt="Pageant icon in notification area" />
	
	Double-clicking the Pageant icon will show you the list of keys Pageant is currently remembering for you. If you set up your shortcut correctly, your GitHub key should already be in the list.
		
	<img src="/images/bootcamp/bootcamp_1_pageant_5.jpg" width="501" height="353" alt="Pageant key list" />

	If you want, you can move or copy your Pageant shortcut to the Start Menu's "Startup" folder, so that it will run whenever you log onto Windows.
	
4. <span class="step-title">Test everything out.</span>

	To make sure everything is working, you&rsquo;ll now SSH to GitHub. Run the main PuTTY client, and type "git@github.com" into the Host Name box, set "Close window on exit" to "Never" so that you can see the messages GitHub displays, and click OK.
	
	<img src="/images/bootcamp/bootcamp_1_putty_test_1.jpg" width="456" height="438" alt="Main PuTTY window" />
	
	PuTTY will the pop up a "Security Alert":
	
	<img src="/images/bootcamp/bootcamp_1_putty_test_2.jpg" width="435" height="294" alt="PuTTY Security Alert" />
	
	Don&rsquo;t worry, this is supposed to happen. Click &ldquo;Yes&rdquo;.
		
	<img src="/images/bootcamp/bootcamp_1_putty_test_3.jpg" width="542" height="340" alt="Success!" />
		
	That's it, you're all set!

##<span class="step">Then: </span> Set Up Your Info

Now that you have Git set up and your SSH keys entered into GitHub, it&rsquo;s time to configure your personal info. First, you need to open Git Bash (not the Windows command line), found in the start menu in the "git" folder.

<img src="/images/bootcamp/bootcamp_1_win_gitbash.jpg" width="558" height="300" alt="Open the terminal" />

<div class="more-info">
  <h4 class="compressed">Need a quick lesson about Git Bash?</h4>
  <div class="more-content">
    <p>Code blocks like those on this page are part of a scripting language called Bash. To use Bash scripts, we need to use an application that was installed with Git called Git Bash.</p>

    <h4>Input</h4>
    <pre class="terminal bootcamp">
      <span class="codeline">$ echo 'This is input text'<span>This tooltip tells you what's going on.</span></span>
    </pre>

    <p>A line that begins with the dollar sign ($) indicates a line of Bash script you need to type. To enter it, type the text that follows the $, hitting the return key at the end of each line. You can hover your mouse over each line for an explanation of what the script is doing.</p>

    <h4>Output</h4>
    <pre class="terminal bootcamp">
      <span class="bash-output">This is output text.</span>
    </pre>

    <p>A line that does not begin with a $ is output text that is intended to give you information or tell you what to do next. We&rsquo;ve colored output text green in these bootcamp tutorials.</p>

    <h4>User Specific Input</h4>
    <pre class="terminal bootcamp">
      <span class="codeline">$ echo '<em>username</em>'<span>Outputs the text in the quotation marks.</span></span>
    </pre>

    <p>Areas of yellow text represent your own personal info, repos, etc. If it is part of an input ($) line, you should replace it with your own info when you type it. If it is part of output text, it is just for your reference. It will automatically show your own info in Git Bash.</p>

    <p><strong>Good to know</strong>: There will be times when you type code, hit return, and all you are given is another prompt. Some actions that you execute in Git Bash don&rsquo;t have any output. Don&rsquo;t worry, if there is ever a problem with your code, Git Bash will let you know.</p>

    <p><strong>Good to know</strong>: For security reasons, Git Bash will not display what you type when entering passwords. Just type your password and hit the return key.</p>
  </div>
</div>

{% include email_setup.markdown %}

##<span class="step">Lastly:</span> Celebrate

Congratulations, you now have Git and GitHub all set up! What do you want to do next?

<ol class="next-steps">
<li>Set Up Git</li>
<li><a href="/create-a-repo/">Create A Repository</a></li>
<li><a href="/fork-a-repo/">Fork A Repository</a></li>
<li><a href="/be-social/">Be Social</a></li>
</ol>
<script>
  $('#os').html("<b>" + $.client.os + "</b>");
</script>
