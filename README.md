prosody-captcha
======

**Introduction**

Prosody-captcha is a little modification for standard prosody's module "mod_register.lua" that provides captcha protection for registration form.

**Installation**

First of all you should build and install lua bindings for libgd — [lua-gd](https://github.com/ittner/lua-gd/).

Then clone repsository lua-captcha:

```git clone https://github.com/mrDoctorWho/lua-captcha```

install it:

```make install```

After that you have to configure prosody. This module requires from you 5 fields, you must add this into your VirtualHost entry.

```lua
captcha_config = {
		dir = "/tmp"; -- Directory used to storage captcha images. Please make sure prosody user allowed to write there.
		timeout = 60; -- Timeout when captcha will expire
		web_path = "challenge"; -- Web path used to separate main prosody site from itself modules.
		font = "/usr/lib/prosody/FiraSans-Regular.ttf"; -- Font used for the captcha text
		quality = 60; -- The captcha quality percentage
	}
```

You can run script "install.lua" to install this. Also you might want to do it manually. Then you need to replace standard prosody "dataforms.lua", which is usually located in "/usr/lib/prosody/util" by another one from this repository. You should do the same thing with "mod_register.lua" located in "/usr/lib/prosody/modules".

After this all you can try to register on the your server and see the captcha.
