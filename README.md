prosody-captcha
======

**Introduction**

Prosody-captcha is a little modification for standard prosody's module *mod_register* that provides captcha protection for registration form.

**Installation**

First of all you should build and install lua bindings for libgd — [lua-gd](https://github.com/ittner/lua-gd/).

Then clone repsository lua-captcha:

```bash
git clone https://github.com/mrDoctorWho/lua-captcha
```

install it:

```bash
make install
```


There are two ways to install the module in your prosody:

**Automatically**:
To install the module automatically, run the script named *install.lua* (Works only if prosody is placed in */usr/lib/*).

**Manually**:

Modules and libraries are usually located in */usr/lib/prosody/modules*.

You need to replace the standard prosody library called *dataforms.lua* and the module *mod_register.lua* by the ones from this repository.

Then prosody should be configured. This module requires 5 fields that must be added into VirtualHost entry:

```lua
captcha_config = {
		dir = "/tmp"; -- Directory used to store the images. Please make sure the prosody user is allowed to write there.
		timeout = 60; -- Timeout of the captcha expiration
		web_path = "challenge"; -- Web path used to separate main prosody site from modules.
		font = "/usr/lib/prosody/FiraSans-Regular.ttf"; -- Font used for the captcha text
		quality = 60; -- The captcha quality percentage
}
```

Prosody captcha is ready!
