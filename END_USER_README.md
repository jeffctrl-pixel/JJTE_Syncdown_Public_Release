# Syncdown end-user guide

Syncdown keeps separate copies of a folder synchronized through a central
server. No Python installation is required when using the executables in
`bin`.

## Set up the server

Copy `syncdown-server-setup.exe` and `syncdown-server.exe` into the same
directory on the computer that will host the server. Run:

```powershell
.\syncdown-server-setup.exe
```

Answer the prompts for bind address, port, repository ID, and a server
password. The defaults are `0.0.0.0`, `8000`, and `demo`. Setup creates or
reuses the repository, stores data in `syncdown-server-data`, creates
`syncdown-server-run.cmd`, starts it, and deletes the setup executable. Use
the run script for later starts. Keep the run executable, configuration, run
script, and data folder together.

The setup output includes a server identification key. Keep it private with
the server password because both are required to create repositories remotely.
Use `127.0.0.1` for local-only use and `0.0.0.0` when other devices need to
connect. Clients must use the server computer's hostname or IP address.

## Set up a client folder

Copy `syncdown-client-setup.exe` and `syncdown-client.exe` into the same
directory on each client computer. Run:

```powershell
.\syncdown-client-setup.exe
```

Answer the prompts for the local folder, repository, server URL, and password.
Setup writes `.syncdown\config.json`, copies the run executable into the
selected folder, creates `syncdown-client-run.cmd`, runs the first sync, and
deletes the setup executable. Use `syncdown-client-run.cmd` for later syncs.

Each device must use its own local folder. Syncdown reports conflicts rather
than silently overwriting either side. TLS is not managed by Syncdown; use
HTTPS through a trusted reverse proxy or a private network.
