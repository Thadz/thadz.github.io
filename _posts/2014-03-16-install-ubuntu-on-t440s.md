---
layout: post
title: "Install Ubuntu On T440s"
categories: article
tags: t440s, thinkpad, ubuntu
---

Recently I bought a Thinkpad T440s. The latest Windows 8.1 looks really gorgeous, but it is so different from any previous version that I am almost using a whole new OS. Given that I seldom use Windows for development, I decided to only install Ubuntu on my laptop. The process of installing is nothing new, except that one needs to remember to disable all UEFI settings in BIOS. Otherwise, the computer wouldn't load Ubuntu. 

# Disable UEFI settings

When the compter starts, press **ENTER** or **F1** to go to the **BIOS** menu. Then go to **Security** page, select **Secure Boot**, disable **Secure Boot**. Later, go back to the top level, and go to **Startup** page, change **UEFI/Legacy Boot** to **Both** and **UEFI/Legacy Boot Priority** to **Legacy First**. You may also need to tweak the **Boot** order for loading the installation media.

# [Thinkpad Touchpad Driver] (https://github.com/ScottGarman/thinkpad_t440s)
By default, the touchpad doesn't support middle key etc. To add the support for this, we need to first deactivate gnome settings by

{% highlight bash %}
sudo apt-get install dconf-editor
{% endhighlight %}

Then, uncheck the "active" option in **org.gnome.settings-daemon.plugins.mouse**.

Now create a file named as **99-synaptics-t440s.conf** under **/etc/X11/xorg.conf.d/** and paste the following in the file.

{% highlight bash %}
# Custom xorg.conf.d snippet that assigns the touchpad driver
# to all touchpads. See xorg.conf.d(5) for more information on
# InputClass.
# Additional options may be added in the form of
#   Option "OptionName" "value"
#
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
      MatchDevicePath "/dev/input/event*"

      # This sets the top area of the touchpad to not track
      # movement but can be used for left/middle/right clicks
      Option "SoftButtonAreas" "60% 0 0 2400 40% 60% 0 2400"
      Option "AreaTopEdge" "2400"

      # Helps to reduce mouse cursor "jumpiness"
      Option "HorizHysteresis" "30"
      Option "VertHysteresis" "30"

      # Settings reported to work well on an X1 Carbon
      Option "FingerLow" "40"
      Option "FingerHigh" "45"
      Option "MinSpeed" "1"
      Option "MaxSpeed" "1"
      Option "AccelerationProfile" "2"
      Option "ConstantDeceleration" "4"

      # Disable edge scrolling, I prefer two-finger scroll instead
      Option "VertEdgeScroll" "0"

      # Disable tap and drag gesture
      Option "TapAndDragGesture" "0"

      # Enable three-finger tap for middle mouse click
      Option "TapButton3" "2"
EndSection
{% endhighlight %}

Now you should be able to use the middle key on the top of the touchpad. More coveniently, tap the touchpad with three fingers can also function as the middle key pressing.

# [Setting Charging Threshold] (https://github.com/teleshoes/tpacpi-bat)

According to the recent discussion in Lenovo forum, the feature to set the charging threshold has been removed in Windows 8. Luckily in Linux, we are still able to set such threshold by altering the modules in the kernel. 

For me, I prefer batteries to start to charge below 60% and stop above 90%. So I simply put
{% highlight bash %}
tpacpi-bat -s ST 1 60
tpacpi-bat -s SP 1 90
tpacpi-bat -s ST 2 60
tpacpi-bat -s SP 2 90
{% endhighlight %}


# Swap Ctrl with Caps Lock and Alt with Tab

As a heavy Emacs user, the swapping is a must. First we can type

{% highlight bash %}
sudo apt-get install xkeycaps
{% endhighlight %}

Next, invoke the key-map tweaker by

{% highlight bash %}
xkeycaps
{% endhighlight %}

After remapping the key positions, put the following in **~/.profile**

{% highlight bash %}
xmodmap ~/.xmodmap-`uname -n`
{% endhighlight %}

# Other miscs:
* Numix theme
* apt-fast
* zsh and oh-my-zsh
* rxvt-unicode

{% highlight bash %}
sudo update-alternatives --config x-terminal-emulator
gsettings set org.gnome.desktop.default-applications.terminal exec 'urxvt'
{% endhighlight %}

* keylock-indicator and cpufreq-indicator
* gitconfig