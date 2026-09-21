# Syncdown releases

This repository contains the Windows end-user and server administrator
executables for Syncdown. It intentionally does not contain the private
development source.

## Client setup and run

Keep these two files together, run setup once, and then use the generated run
script:

```powershell
.\syncdown-client-setup.exe
.\syncdown-client-run.cmd
```

Setup asks for the local folder, server URL, repository, and password. It
creates `.syncdown\config.json`, copies `syncdown-client.exe` into the local
folder, runs the first sync, and deletes `syncdown-client-setup.exe`.

## Server setup and run

Keep `syncdown-server-setup.exe` and `syncdown-server.exe` together and run:

```powershell
.\syncdown-server-setup.exe
.\syncdown-server-run.cmd
```

Setup configures the bind address, port, repository, and server password. It
creates the server data and configuration files, starts the server, and
deletes `syncdown-server-setup.exe`. Later starts use the generated run script.
The server stores SQLite metadata and content-addressed objects under the data
directory. The setup output includes the server identification key for
administrative repository creation.

See [END_USER_README.md](./END_USER_README.md) for the complete setup guide.
