Manually:

```powershell
Set-Location C:\users\test\Desktop\azure-devops
python .\setup install
```
Get from local repo:
```powershell
pip3 install twine --index-url=https://<username>:<password>@<host>/repository/<repository_name>/simple
```
For more information:
https://stackoverflow.com/questions/60814982/how-to-setup-pip-to-download-from-mirror-repository-by-default
