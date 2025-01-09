# Comandos personalizados do PowerShell

```ps1
$MaximumHistoryCount = 2000

# Import-Module posh-git
# Import-Module PSReadLine
# Import-Module Get-ChildItemColor
# Import-Module Terminal-Icons
# Import-Module DockerCompletion



# Configuração tema
## Melhores:
  # material
  # spaceship
  # Usar Get-PoshThemes para ver mais opcoes
    # Alterar o nomeDoTema.omp.json na linha abaixo
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH/material.omp.json" | Invoke-Expression

# Uses tab for autocompletion
Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete

# History definitions
$HistoryFilePath = Join-Path ([Environment]::GetFolderPath('UserProfile')) .ps_history
Register-EngineEvent PowerShell.Exiting -Action { Get-History | Export-Clixml $HistoryFilePath } | out-null
if (Test-path $HistoryFilePath) { Import-Clixml $HistoryFilePath | Add-History }

Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadlineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadlineKeyHandler -Key DownArrow -Function HistorySearchForward

Set-PSReadLineOption -ShowToolTips
Set-PSReadLineOption -PredictionSource History

# Aliases
Set-Alias which Get-Command
Set-Alias open Invoke-Item

function ll() { Get-ChildItem | Format-Table }
function la() { Get-ChildItem | Format-Wide }
function lb() { Get-ChildItem | Format-List }

Set-Alias ls la
Set-Alias l lb

# Aliases Functions

function profile() { code $PROFILE }
function edh() { code "$HOME\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt" }
function eds() { code "$HOME\AppData\Local\oh-my-posh\spaceship.omp.json" }

# Compute file hashes - useful for checking successful downloads
function md5    { Get-FileHash -Algorithm MD5 $args }
function sha1   { Get-FileHash -Algorithm SHA1 $args }
function sha256 { Get-FileHash -Algorithm SHA256 $args }

function tail { Get-Content $args -Tail 30 -Wait }

function take {
  New-Item -ItemType directory $args
  Set-Location "$args"
}
# Minhas funcoes
function meuip(){  
  Get-NetIPAddress -AddressFamily IPv4 | Select-Object InterfaceAlias, IPAddress, PrefixLength
}
function new-venv(){  
  "Execultando: virtualenv venv"
  pip install virtualenv
  virtualenv venv
  ative-venv
}
function ative-venv(){  
  "Execultando: venv/Scritps/activate"
  venv/Scripts/activate
  python.exe -m pip install --upgrade pip
}
function freeze-save(){  
  "Execultando: pip freeze > requirements.txt"
  pip freeze > requirements.txt
}
function freeze-install(){  
  "Execultando: pip install -r requirements.txt"
  pip install -r requirements.txt
}
# Comandos DJANGO
function django-init(){
  "Executando: django-admin startproject setup ."
  django-admin startproject setup .
}
function django-app($appName){
  "Executando: django-admin startapp $appName"
  django-admin startapp $appName
}
 
function pmr(){  
  "Execultando: python manage.py runserver"
  python manage.py runserver
}
function django-tables(){
  "Execultando: python manage.py makemigrations"
  python manage.py makemigrations
  "Execultando: python manage.py migrate"
  python manage.py migrate
}

```
# Configurações
Basta copiar e colar o settings.json para a pasta de configuração de usuario do vsCode
# Extenções
Basta copiar e colar o extensions.json para a pasta de confifuração do usuario do vsCode\
Talvez seja necessario alteração do path de usuario
