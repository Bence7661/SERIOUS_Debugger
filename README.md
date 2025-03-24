# Debugger
A little tool that displays specific log messages real time in a console window.  
I use this tool basically all the time while developing mods. It helped me increase my productivity greatly since I get to select what logs are important and I don't need to keep opening the console to see them.  
I can just set up Anomaly/G.A.M.M.A. on 1 monitor. This debugger on the other and it's ready to go.

It's pretty resilient to values passed to it. A `nil` won't crash it and if you fcked up formatting instead of crashing it will just log a message saying so.

# Setup
There are a few steps to make it work properly.
1. Install the mod (priority doesn't matter at all).
2. Open `FileLogger.script` and modify the `log_file_path` variable. Set this to wherever you want your logs to go (and copy it because you'll need it in the next step).
3. Open `LogViewer.bat` and replace `<PATH HERE>` with the path you set in `FileLogger.script`. Don't paste as a string! so don't paste it between `""` symbols. Just like this: `C:\ModdingCustomLogs\G.A.M.M.A\custom_log.txt`

Now you can test if it works. Open up `LogViewer.bat` (It should be completely empty). Then navigate to the path you specified. 
Create the `.txt` file. Open it, write something in it then save it.

# Usage in Lua code
Just call `FileLogger.log(template, arguments)`.  

Example:
```lua
function Foo()
  -- Some beautiful script written by you.

  local testVariable = 25
  local otherVariable = nil
  FileLogger.log("Test variable is: %s, other variable is: %s", testVariable, otherVariable)
end
```

The debugger should show a log like
```cmd
[2025-03-23 20:59:19] Test variable is: 25, other variable is: nil
```

# Cleaning
You should just nuke the `custom_log.txt` (or whatever name you choose) file because it's never emptied by the debugger itself.  
Maybe in the future I'll add a keybind that when pressed will delete every line of log from `custom_log.txt`.

# Example screenshot
This is my logger window while I was developing the newest version of `The Job Can Wait`.  
Don't mind what the logs actually say in the picture below.
  
![image](https://github.com/user-attachments/assets/ab96ec01-3f0c-42c3-8d7e-2c703985affa)
