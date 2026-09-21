# Syncdown end-user guide

Syncdown keeps separate copies of a folder synchronized through a central
server. Download `bin\syncdown.exe` from this repository and follow the instructions
below.

1. Create a local folder for this device.
2. Create `.syncdown\config.json` inside it with the repository ID and server
   URL supplied by the server administrator.
3. Run `bin\syncdown.exe "C:\path\to\your\folder"`.

Each device must use its own local folder. Syncdown reports conflicts rather
than silently overwriting either side.
