# Syncdown releases

This repository contains the Windows end-user and server administrator
executables for Syncdown. It intentionally does not contain the private
development source.

## Client

Configure a local folder with `.syncdown\config.json` and run:

```powershell
.\bin\syncdown.exe "C:\Syncdown\SharedProject"
```

The configuration format is:

```json
{
  "repository": "shared-project",
  "server": "http://192.168.1.20:8000"
}
```

## Server administrator

Start the server with:

```powershell
.\bin\syncdown-server.exe --host 0.0.0.0 --port 8000 --data-dir .\syncdown-server-data
```

Create repositories through the server's `POST /repositories` API. The server
stores SQLite metadata and content-addressed objects under the selected data
directory. Do not expose this prototype to an untrusted network without
adding authentication, authorization, and TLS.

See [END_USER_README.md](./END_USER_README.md) for the complete setup guide.
