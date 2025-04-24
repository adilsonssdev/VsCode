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
# Linha comentada devido à incompatibilidade
# Set-PSReadLineOption -PredictionSource History

# Aliases
Set-Alias which Get-Command
Set-Alias open Invoke-Item

function ll() { Get-ChildItem | Format-Table }
function la() { Get-ChildItem | Format-Wide }
function lb() { Get-ChildItem | Format-List }

# Set-Alias ls la -Force
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
  "
  Criando ambiente virtual: 'venv'
  python -m venv venv
  "
  python -m venv venv
  ative-venv
}
function ative-venv(){  
  "
  Ativando ambiente virtual: 'venv'
  venv/Scritps/activate
  "
  venv/Scripts/activate
  att-pip
}
function att-pip(){
  "
  Atualizando pip
  python.exe -m pip install --upgrade pip
  "
  python.exe -m pip install --upgrade pip
  freeze-install
}

function freeze-save(){  
  "Execultando: pip freeze > requirements.txt"
  pip freeze > requirements.txt
}
function freeze-install(){  
  "
  Verificando e instalando pacotes
  pip install -r requirements.txt
  "
  pip install -r requirements.txt
  clear
}
