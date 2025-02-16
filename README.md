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
```
La tâche que j'ai faite est la suivante:

Mettre les fichiers avec un numéro pair dans un dossier c:\EvenFolder

Mettre les fichiers avec un numéro impair dans un dossier c:\OddFolder

```powershell
# Définir les dossiers de destination
$evenFolder = "C:\EvenFolder"
$oddFolder = "C:\OddFolder"

# Créer les dossiers s'ils n'existent pas
New-Item -ItemType Directory -Path $evenFolder -Force
New-Item -ItemType Directory -Path $oddFolder -Force

# Déplacer les fichiers selon leur numéro
$allFiles = Get-ChildItem -Path C:\FolderTest1, C:\FolderTest2 -File

foreach ($file in $allFiles) {
    if ($file.Name -match "File(\d+)") {
        $num = [int]$matches[1]
        if ($num % 2 -eq 0) {
            Move-Item -Path $file.FullName -Destination $evenFolder -Force
        } else {
            Move-Item -Path $file.FullName -Destination $oddFolder -Force
        }
    }
}

Write-Output "Les fichiers ont été déplacés avec succès."
