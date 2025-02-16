# PowerShell : 2 L'arborescence et les fichiers

J'ai copié le code ci-dessous dans la fenêtre script de PowerShell ISE et l'executer (F5) :
```powershell
Set-Location -Path C:\
#Une écriture possible pour la création d'un dossier
New-Item -ItemType Directory -Path C:\ -Name FolderTest1
#Une autre écriture possible pour la création d'un dossier
New-Item -ItemType Directory -Path C:\FolderTest2
#Création de fichier vide dans le dossier c:\FolderTest
New-Item -ItemType File -Path C:\FolderTest1 -Name File1
New-Item -ItemType File -Path C:\FolderTest1 -Name File2
New-Item -ItemType File -Path C:\FolderTest1 -Name File3
New-Item -ItemType File -Path C:\FolderTest1 -Name File4
New-Item -ItemType File -Path C:\FolderTest1 -Name File5
#Création de fichier vide dans le dossier c:\FolderTest2
$Count = 6
Do
{
    New-Item -ItemType File -Path C:\FolderTest2 -Name "File$Count"
    $Count++
}
While ($Count -lt 11)
