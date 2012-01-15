---
layout: default
title: Set Up Git Using PuTTY
description: An alternative guide to getting started with Git using the PuTTY family of tools
---

<p class="intro">If you&rsquo;ve found yourself on this page, we&rsquo;re assuming you&rsquo;re brand new to Git and GitHub. This guide will walk you through the basics and explain a little bit about how everything works along the way.</p>

<p class="intro">This is the guide for setting up git in <strong>Windows</strong> using the PuTTY family of tools (including Puttygen, Pageant, and Plink). The <strong><a href="/win-set-up-git">official guide for Windows set up</a></strong> uses "openssh"; there are also guides for <strong><a href="/mac-set-up-git">OSX</a></strong> and <strong><a href="/linux-set-up-git">Linux</a></strong>.</p>

##<span class="step">First:</span> Download and Install PuTTY and Git

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

    <img src="/images/bootcamp/bootcamp_1_win_install_1.jpg" width="558" height="442" alt="Welcome page" />
    <img src="/images/bootcamp/bootcamp_1_win_install_2.jpg" width="558" height="442" alt="Information" />
    <img src="/images/bootcamp/bootcamp_1_win_install_3.jpg" width="558" height="442" alt="Select destination location" />
    <img src="/images/bootcamp/bootcamp_1_win_install_4.jpg" width="558" height="442" alt="Select start menu folder" />
    <img src="/images/bootcamp/bootcamp_1_win_install_5.jpg" width="558" height="442" alt="Select components" />
    <img src="/images/bootcamp/bootcamp_1_win_install_6.jpg" width="558" height="442" alt="Adjusting your PATH environment" />
    <img src="/images/bootcamp/bootcamp_1_win_install_6a.jpg" width="558" height="442" alt="Choosing the SSH executable" />
    <img src="/images/bootcamp/bootcamp_1_win_install_7.jpg" width="558" height="442" alt="Configuring the line ending conversions" />
    <img src="/images/bootcamp/bootcamp_1_win_install_8.jpg" width="558" height="442" alt="Installing" />
    <img src="/images/bootcamp/bootcamp_1_win_install_9.jpg" width="558" height="442" alt="Installation complete" />
  </li>
</ol>

##<span class="step">Next:</span> Set Up SSH Keys

We use SSH keys to establish a secure connection between your computer and GitHub. Setting them up is fairly easy, but does involve a number of steps.

[TODO: Pageant instructions here...]

##<span class="step">Then: </span> Set Up Your Info

Now that you have Git set up and your SSH keys entered into GitHub, it&rsquo;s time to configure your personal info.

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
