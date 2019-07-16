---
title: Ciągi podstawienia używane w. Pkgdef i. Pliki Pkgundef | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160536"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Ciągi podstawienia używane w plikach .Pkgdef i .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć ciągów podstawienia wymienione poniżej w pkgdef i pkgundef plików, należy zdefiniować dla programu Visual Studio isolated shell aplikacji.  
  
## <a name="substitution-strings"></a>Ciągi podstawienia  
  
|String|Opis|  
|------------|-----------------|  
|$=*RegistryEntry*$|Wartość *RegistryEntry* wpisu. Jeśli ciąg wpis rejestru kończy się znakiem ukośnika odwrotnego (\\), zostanie użyta domyślna wartość podklucza rejestru. Na przykład podstawienia ciągu $= HKEY_CURRENT_USER\Environment\TEMP$ jest rozwinięty folder tymczasowy bieżącego użytkownika.|  
|$AppName$|Kwalifikowana nazwa aplikacji, który jest przekazywany do AppEnv.dll punkty wejścia. Kwalifikowana nazwa składa się z nazwy aplikacji, podkreślenia i identyfikator klasy (CLSID) obiektu automatyzacji aplikacji, który jest zarejestrowany jako wartość ustawienia ThisVersionDTECLSID w pliku .pkgdef projektu.|  
|$AppDataLocalFolder|Podfolderu w folderze % LOCALAPPDATA % dla tej aplikacji.|  
|$BaseInstallDir$|Pełna ścieżka lokalizacji, w którym zainstalowano program Visual Studio.|  
|$CommonFiles$|Wartość zmiennej środowiskowej % CommonProgramFiles %.|  
|$MyDocuments$|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika.|  
|$PackageFolder$|Pełna ścieżka katalogu, który zawiera pliki zestawu pakietu dla aplikacji.|  
|$ProgramFiles$|Wartość zmienna środowiskowa % ProgramFiles %.|  
|$RootFolder$|Pełna ścieżka katalogu głównego aplikacji.|  
|$RootKey$|Główny klucz rejestru dla aplikacji. Domyślnie katalog główny jest w HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*Numerwersji* (gdy Aplikacja jest uruchomiona, _Config jest dołączany do tego klucza). Jest on ustawiony przez wartość RegistryRoot *SolutionName*plik .pkgdef.<br /><br /> Ciąg $ $RootKey może służyć do pobierania wartości rejestru w podkluczu aplikacji. Na przykład ciąg "$= $RootKey \AppIcon$" zwróci wartość AppIcon wpis w podkluczu katalogu głównego aplikacji.<br /><br /> Analizator przetwarza sekwencyjnie plik .pkgdef i będą mogli wpisu rejestru w podkluczu aplikacji tylko wtedy, gdy wpis został wcześniej zdefiniowany|  
|$ShellFolder$|Pełna ścieżka lokalizacji, w którym zainstalowano program Visual Studio.|  
|$System$|Do folderu Windows\system32.|  
|$WINDIR$|Windows folder.|  
  
 Jeżeli Analizator nie rozpoznaje ciąg podstawienia nie może ustalić wartości wpisu rejestru lub zmienną środowiskową, a następnie podstawienia nie są wykonywane w tej części ciągu.
