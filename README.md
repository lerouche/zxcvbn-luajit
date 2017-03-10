# LuaJIT C module for zxcvbn-c

This is a LuaJIT module that uses LuaJIT's C APIs to allow the usage of [zxcvbn-c](https://github.com/tsyrogit/zxcvbn-c) within Lua code as a library. It should be easily ported to standard Lua, but this has not been tested.

## Building

```bash
cd /path/to/this/repo
./build.sh "/path/to/luajit/includes"
mv zxcvbn.so /path/to/lua/modules/zxcvbn.so
```

Note that you **must** place the compiled `zxcvbn.so` in your Lua's [require path](https://www.lua.org/pil/8.1.html) so that `require('zxcvbn')` loads the library -- using any other path such that `'zxcvbn'` is not the `require` argument value won't work. This is because the library name is hard-coded in the C module, a requirement for making Lua C modules.

## Using

```lua
local zxcvbn = require('zxcvbn')

-- The variable `entropy` will be a number, and may have decimal places
local entropy = zxcvbn.getEntropy("password", {"optional", "user", "dictionary"})
```

## Differences from the original version

See the upstream repository's README.md at https://github.com/tsyrogit/zxcvbn-c

##References

The original version by Dropbox is available at https://github.com/lowe/zxcvbn

The C version this is based from is available at https://github.com/tsyrogit/zxcvbn-c
