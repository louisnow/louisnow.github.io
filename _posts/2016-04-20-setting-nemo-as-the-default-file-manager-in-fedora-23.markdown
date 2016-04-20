---
title: Setting Nemo as the Default File Manager in Fedora 23
layout: post
comments: true
permalink: setting-nemo-as-the-default-file-manager-in-fedora-23
---
Fedora is great, Gnome 3 is alright but the default file manager Nautilus seems lacking out of the box. You have two choices here, either customize Nautilus heavily using extensions or install something else that for most purposes just works. After looking at all the available file managers, I settled on Nemo which is the official file manager of the Cinnamon desktop. In my opinion it's the best there is. I should also note that Nemo was the only thing I missed when I made the switch from Mint to Fedora.

Unfortunately Fedora lacks an option in the Settings > Details > Default Applications menu for a file manager. Hopefully they'll add this feature soon.

## Installation

First install Nemo and a customization tool called Alacarte.

{% highlight shell %}
sudo dnf install nemo alacarte
{% endhighlight %}

Now, according to this [StackOveflow answer](https://ask.fedoraproject.org/en/question/9759/how-do-i-use-the-nemo-file-browser-as-default-instead-of-nautilus/), you should be able to set nemo as your default file manger through Alacarte itself. I'd recommend you try that method first before continuing. In my case, that didn't work.

The following command will force Nemo to be the default file manager in most circumstances. 

{% highlight shell %}
xdg-mime default nemo.desktop inode/directory
{% endhighlight %}

So when you open folders from a browser, it will now use nemo instead of nautilus. Although certain applications will use nautilus at times. It is because of this that I recommend to not uninstall Nautilus to avoid weird bugs.

Now to create an icon for nemo in the applications menu.
Open Alacarte, select Accessories > New Item

Set the command to 
{% highlight shell %} 
/usr/bin/nemo
{% endhighlight %}
To get the icon for Nemo, navigate to
{% highlight shell %} 
/usr/share/icons/gnome/256x256/places/folder.png
{% endhighlight %}

![Nemo](/assets/nemo.png)

Note : If you click browse in Alacarte, it will use Nautilus instead of Nemo. Removing nautilus might cause this to break. If you've tried it and everything is fine, do let me know in the comments.

You can now add Nemo to your favourites list in the Gnome side bar.

{% include twitter_plug.html %}