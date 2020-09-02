---
title: Ciągi podstawienia używane w. Pkgdef i. Pliki PKGUNDEF | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160536"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Ciągi podstawienia używane w plikach .Pkgdef i .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć ciągów podstawienia wymienionych poniżej w plikach. pkgdef i. pkgundef zdefiniowanych dla aplikacji powłoki izolowanej programu Visual Studio.  
  
## <a name="substitution-strings"></a>Ciągi podstawienia  
  
|String|Opis|  
|------------|-----------------|  
|$=*RegistryEntry*$|Wartość wpisu *RegistryEntry* . Jeśli ciąg wpisu rejestru zostanie zakończony ukośnikiem odwrotnym ( \\ ), wówczas zostanie użyta wartość domyślna podklucza rejestru. Na przykład ciąg podstawienia $ = HKEY_CURRENT_USER \Environment\TEMP $ jest rozwinięty do folderu tymczasowego bieżącego użytkownika.|  
|$AppName $|Kwalifikowana nazwa aplikacji, która jest przenoszona do punktów wejścia AppEnv.dll. Kwalifikowana nazwa składa się z nazwy aplikacji, podkreślenia i identyfikatora klasy (CLSID) obiektu automatyzacji aplikacji, który jest również rejestrowany jako wartość ustawienia ThisVersionDTECLSID w pliku Project. pkgdef.|  
|$AppDataLocalFolder|Podfolder w lokalizacji% LOCALAPPDATA% dla tej aplikacji.|  
|$BaseInstallDir $|Pełna ścieżka lokalizacji, w której zainstalowano program Visual Studio.|  
|$CommonFiles $|Wartość zmiennej środowiskowej% CommonProgramFiles%.|  
|$MyDocuments $|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika.|  
|$PackageFolder $|Pełna ścieżka katalogu zawierającego pliki zestawu pakietu dla aplikacji.|  
|$ProgramFiles $|Wartość zmiennej środowiskowej% ProgramFiles%.|  
|$RootFolder $|Pełna ścieżka katalogu głównego aplikacji.|  
|$RootKey $|Klucz rejestru głównego dla aplikacji. Domyślnie katalog główny znajduje się w HKEY_CURRENT_USER \Software \\ *CompanyName* \\ *ProjectName* \\ *versionNumber* (gdy aplikacja jest uruchomiona, _Config jest dołączany do tego klucza). Jest on ustawiany przez wartość RegistryRoot w pliku *SolutionName*. pkgdef.<br /><br /> Ciąg $RootKey $ może służyć do pobrania wartości rejestru w podkluczu aplikacji. Na przykład ciąg "$ = $RootKey $ \AppIcon $" zwróci wartość wpisu AppIcon w podkluczu głównym aplikacji.<br /><br /> Parser przetwarza plik pkgdef sekwencyjnie i może uzyskać dostęp do wpisu rejestru w podkluczu aplikacji tylko wtedy, gdy wpis został wcześniej zdefiniowany.|  
|$ShellFolder $|Pełna ścieżka lokalizacji, w której zainstalowano program Visual Studio.|  
|$System $|Folder Windows\System32.|  
|$WINDIR $|Folder systemu Windows.|  
  
 Jeśli analizator składni nie rozpoznaje ciągu podstawiania lub nie może ustalić wartości wpisu rejestru lub zmiennej środowiskowej, nie wykonuje podstawienia dla tej części ciągu.
