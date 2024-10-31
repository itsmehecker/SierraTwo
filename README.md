# SierraTwo (files modified so you can build on windows instead of linux)
`SierraTwo` is a simple reverse shell over Slack. 

<p align="center">
  <img src="media/demo.gif">
</p>

## Usage
`SierraTwo` only supports Python 3.6+. (better you use the 3.8 it worked perfectly for me)
link to [python 3.8](https://www.python.org/ftp/python/3.8.2/python-3.8.2-amd64.exe)

### Direct Usage
#### Windows
```
pip3 install -r requirements.txt 
python3 SeirraTwo.py
```
### Building
To build an executable:

for windows:
```
> pip3 install -r requirements.txt
> pyarmor-7 pack -e --onefile --icon media/msdtc.ico -n msdt SierraTwo.py
```
This will create a dist directory in which there will be the final .exe


Both executables will be obfuscated using `pyarmor`.

If built for Windows:
- The executable's name will be `msdtc.exe`
- Executable will automatically minimize and hide itself


## Configuration
Directly edit the variables(member id,Oath token etc) in the *SeirraTwo.py* as importing config.py gave some errors 
To use `SierraTwo`, create or be a part of a Slack workspace where you an admin. Afterwards go to 
[Slack API][Slack API] and create an app. From there, under the `Features` tab, go to `OAuth & Permissions` and add the 
following scopes:

### Bot Token Scopes
| Permission             | Description                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------|
| **channels:history**   | View messages and other content in public channels that BravoOmegaTango has been added to       |
| **channels:join**      | Join public channels in the workspace                                                           |
| **channels:manage**    | Manage public channels that BravoOmegaTango has been added to and create new ones               |
| **channels:read**      | View basic information about public channels in the workspace                                   |
| **chat:write**         | Send messages as @bravoomegatango                                                               |
| **commands**           | Add actions and/or slash commands that people can use                                           |
| **files:write**        | Upload, edit, and delete files as BravoOmegaTango                                               |
| **groups:history**     | View messages and other content in private channels that BravoOmegaTango has been added to      |
| **groups:read**        | View basic information about private channels that BravoOmegaTango has been added to            |
| **groups:write**       | Manage private channels that BravoOmegaTango has been added to and create new ones              |
| **im:history**         | View messages and other content in direct messages that BravoOmegaTango has been added to       |
| **im:read**            | View basic information about direct messages that BravoOmegaTango has been added to             |
| **im:write**           | Start direct messages with people                                                               |
| **mpim:history**       | View messages and other content in group direct messages that BravoOmegaTango has been added to |
| **mpim:read**          | View basic information about group direct messages that BravoOmegaTango has been added to       |
| **mpim:write**         | Start group direct messages with people                                                         |
| **remote_files:write** | Add, edit, and delete remote files on the user’s behalf                                         |

### User Token Scopes
| Permission | Description              |
|------------|--------------------------|
| **admin**  | Administer the workspace |

After setting the token scopes, copy and paste your `Member ID` (and others that will have access to the app), 
`OAuth Access Token` and `Bot User OAuth Token` to `SeirraTwo.py`. Finally, install the app on the workspace.

## Notes
- The shells (or rooms in other words) will be created under the predetermined prefix. You can change this prefix in 
SeirraTwo.py
- Upon launch, `SierraTwo` will connect to the workspace and look for channels matching the prefix. If there are no 
channels matching the prefix, `prefix-1` will be created. By default, this is `sierra-hotel-1`. However, if there is a 
channel (or channels) matching the prefix, `SierraTwo` will get the largest number amongst the matching channels and 
add onto the largest number amongst the channels. That means if `sierra-hotel-5` is the with the largest number amongst 
all present channels, the next channel will be `sierra-hotel-6`.
- You can only run one instance of `SierraTwo` at a given time. This is due to Slack's API. To circumvent this, you can 
create multiple applications in [Slack API][Slack API] and run multiple instances of SierraTwo under different, unique 
tokens.
- To close your current shell, type `shell_exit` in the channel.

## Disclaimers
- This project is for educational purposes only. The developers and contributors are not responsible for any damage 
that may be caused by this program nor any consequences that may arise.
- By using this program you accept that the developers and contributors are not responsible if you violate 
[Slack's Terms of Service][Slack ToS] and [Slack's API Terms of Service][Slack API ToS].
- With the current permissions of the app, `SierraTwo` will have an admin access over your workspace.

## TODO:
- Implement a simple process injection method for Windows and Linux.
- Implement an easy-to-use obfuscated (for evasion. No anti-debugging.) binary generation for Windows and Linux 
operating systems.

[Slack API]:      https://api.slack.com
[Slack ToS]:      https://slack.com/terms-of-service
[Slack API ToS]:  https://slack.com/terms-of-service/api
