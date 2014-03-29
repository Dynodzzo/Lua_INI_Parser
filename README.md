#LIP - Lua INI Parser#
*Lua INI Parser* is a tiny Lua library allowing to handle *.ini* files.

#Usage#
Add [LIP.lua](https://github.com/Dynodzzo/Lua_INI_Parser/blob/master/LIP.lua) file into your project folder.<br />
Call it using __require__ function.<br />
It will return a table containing read & write functions.

#Full overview#
* __LIP.load(fileName)__ : Returns a table containing all the values from the file.
* __LIP.save(fileName, data)__ : Saves the data into the specified file.

#Examples#
Here's how to save some data :

```lua
local LIP = require 'LIP';

local data =
{
	sound =
	{
		left = 70,
		right = 80,
	},
	screen =
	{
		width = 960,
		height = 544,
		caption = 'Window\'s caption',
		focused = true,
	},
};

-- Data saving
LIP.save('savedata.ini', data);
````
And the *.ini* file created :
```ini
[sound]
left=70
right=80

[screen]
width=960
height=544
caption=Window's caption
focused=true
````

Now let's get all this data :

```lua
local LIP = require 'LIP';

-- Data loading
local data = LIP.load('savedata.ini');

print(data.sound.right); --> 80
print(data.screen.caption); --> Window's caption
print(data.screen.focused); --> true
````

It is also possible to give indexes instead of keys :

```lua
local data =
{
	{
		right = 40,
		50,
	},
	{
		'Some text',
		20,
		true,
	},
};
````

And we have to retrieve data using these indexes :

```lua
print(data[1][1]); --> 50
print(data[1].right) --> 40
print(data[2][1]); --> Some text
print(data[2][3]); --> true
````

#Licence#
This project is under [MIT Licence][]<br />
Copyright © Carreras Nicolas

	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:

	The above copyright notice and this permission notice shall be included in all
	copies or substantial portions of the Software.

	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
	SOFTWARE.

[MIT Licence]: http://opensource.org/licenses/MIT
