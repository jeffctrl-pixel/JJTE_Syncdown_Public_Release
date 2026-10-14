# Syncdown end-user guide

Syncdown keeps separate copies of a folder synchronized through a central
server. No Python installation is required when using the Windows
executables in `bin`.

Keep each setup executable beside its matching run executable until setup is
complete. After setup, runtime executables, configuration, and server data
are stored in `.syncdown`; the generated `.bat` launcher is the only
Syncdown-created file that remains visible at the top level.

## Set up the server

Copy `syncdown-server-setup.exe` and `syncdown-server.exe` from `bin` into the
directory that will hold the server installation. Run:

```powershell
.\syncdown-server-setup.exe
```

Answer the prompts for bind address, port, repository ID, and a server
password. The defaults are `0.0.0.0`, `8000`, and `demo`. Setup stores the
runtime executable, configuration, and server data under `.syncdown` in
that directory, creates `syncdown-server-run.bat`, and starts the server.
The setup executable and the original run executable beside it are removed
after startup. Use `syncdown-server-run.bat` for later starts.

You can supply any setup value with `--host`, `--port`, `--repository`, and
`--password`; any option you omit still uses its prompt. For example:

```powershell
.\syncdown-server-setup.exe --host 0.0.0.0 --port 8000 `
  --repository shared-project
```

Add `--password "your-password"` to skip the password prompts. Command-line
passwords may be visible to local process inspection, so use the interactive
prompt for normal manual setup.
For automation that should configure the server without starting it
immediately, add `--no-start` and run the generated
`syncdown-server-run.bat` when ready.

The setup output includes a server identification key. Keep it private along
with the server password; both are required to create repositories remotely.
Use `127.0.0.1` for local-only use and `0.0.0.0` when other devices need to
connect. Clients must use the server computer's hostname or IP address.

## Set up a client folder

Copy `syncdown-client-setup.exe` and `syncdown-client.exe` from `bin` into a
temporary directory and run:

```powershell
.\syncdown-client-setup.exe
```

Answer the prompts for the local folder, repository, server IP address or
hostname, port, and password. You can supply values with `--folder`,
`--repository`, `--host`, `--port`, and `--password`; any omitted option still
uses its prompt. For example:

```powershell
.\syncdown-client-setup.exe --folder "C:\Syncdown\SharedProject" `
  --repository shared-project --host 192.168.1.20 --port 8000
```

Add `--password "your-password"` to skip the password prompt. Command-line
passwords may be visible to local process inspection. To configure the client
without immediately syncing, add `--no-start` and run the generated
`syncdown-client-run.bat` when ready. Setup writes
`.syncdown\config.json` and installs
`syncdown-client.exe` under `.syncdown` in the selected folder. It creates
`syncdown-client-run.bat` at the top level, runs the first sync, and removes
the setup executable from the temporary directory. Use
`syncdown-client-run.bat` for later syncs.

Each device must use its own local folder. Syncdown reports conflicts rather
than silently overwriting either side. Removing a previously synced file
deletes it from the shared repository and other devices on their next sync,
unless another device has changed that file, in which case Syncdown reports a
conflict.

Syncdown identifies a rename when exactly one removed path and one newly
added path have identical file contents (matching SHA-256 hashes). A rename
with changed contents, or ambiguous duplicate contents, is reported as a
deletion and an addition rather than guessed. TLS is not managed by Syncdown;
use HTTPS through a trusted reverse proxy or a private network.
