# Syncdown releases

This repository contains the Windows end-user and server administrator
executables for Syncdown. It intentionally does not contain the private
development source.

The four executables are in [`bin/`](./bin/). Keep each setup executable beside
its corresponding run executable until setup is complete.

## Client setup and run

Copy `syncdown-client-setup.exe` and `syncdown-client.exe` from `bin` into a
temporary directory, then run the setup executable:

```powershell
.\syncdown-client-setup.exe
```

Setup asks for the local folder, server URL, repository, and password. It
creates `.syncdown\config.json` and installs `syncdown-client.exe` under
`.syncdown` in the selected folder. The generated `syncdown-client-run.bat`
launcher remains at the top level of that folder; use it for later syncs.

## Server setup and run

Copy `syncdown-server-setup.exe` and `syncdown-server.exe` from `bin` into the
directory that will hold the server installation, then run the setup
executable:

```powershell
.\syncdown-server-setup.exe
```

Setup configures the bind address, port, repository, and server password. It
installs the runtime executable, configuration, and server data under
`.syncdown` in the setup directory. The generated
`syncdown-server-run.bat` launcher remains at the top level; use it to start
the server later. The setup output includes the server identification key
needed for administrative repository creation.

See [END_USER_README.md](./END_USER_README.md) for the complete setup guide.
