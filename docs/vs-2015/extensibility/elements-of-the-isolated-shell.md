---
title: Elementy powłoki izolowanej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204605"
---
# <a name="elements-of-the-isolated-shell"></a>Elementy programu Shell (izolowanego)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można modyfikować ustawienia rejestru, ustawienia czasu wykonywania oraz punkt wejścia aplikacji izolowanej powłoki oraz pliki. vsct,. pkgdef i. PKGUNDEF.  
  
## <a name="registry-settings"></a>Ustawienia rejestru  
 Pliki. pkgdef i. pkgundef modyfikują ustawienia rejestru dla aplikacji izolowanej powłoki. Po uruchomieniu aplikacji ustawienia rejestru są definiowane w następującej kolejności:  
  
 Po uruchomieniu aplikacji ustawienia rejestru są definiowane w następującej kolejności:  
  
1. Zostanie utworzony klucz rejestru aplikacji.  
  
2. Rejestr jest aktualizowany z pliku. pkgdef aplikacji przez definiowanie określonych kluczy i wpisów.  
  
3. Dla każdego pakietu, który jest częścią aplikacji, rejestr jest aktualizowany z pliku. pkgdef tego pakietu. Każdy pakiet jest zdefiniowany w pliku pkgdef aplikacji przez klucz $RootKey $ \Packages \\ {*vsPackageGuid*} dla pakietu.  
  
4. Rejestr został zaktualizowany z AppEnvConfig. pkgdef i BaseConfig. pkgdef w *ścieżce instalacji zestawu SDK programu Visual Studio*\Common7\IDE\ShellExtensions\Platform. Te pliki są częścią programu Visual Studio, a także częścią pakietu redystrybucyjnego programu Visual Studio Shell (Tryb izolowany).  
  
5. Rejestr został zaktualizowany z pliku. pkgundef aplikacji przez usunięcie określonych kluczy i wpisów.  
  
## <a name="run-time-settings"></a>Ustawienia czasu wykonywania  
 Gdy użytkownik uruchamia izolowaną aplikację powłoki, wywołuje początkowy punkt wejścia powłoki programu Visual Studio. Ustawienia aplikacji są definiowane podczas uruchamiania aplikacji w następujący sposób:  
  
1. Powłoka programu Visual Studio sprawdza rejestr aplikacji pod kątem określonych kluczy. Jeśli ustawienie klucza jest określone w wywołaniu punktu wejścia rozpoczęcia, ta wartość zastępuje wartość w rejestrze.  
  
2. Jeśli żaden z parametrów rejestru lub punktu wejścia nie określa wartości ustawienia, zostanie użyta wartość domyślna ustawienia.  
  
   Gdy użytkownik uruchamia aplikację z wiersza polecenia, wszystkie przełączniki wiersza polecenia są przesyłane do powłoki programu Visual Studio, która traktuje je w taki sam sposób, jak devenv. Aby uzyskać więcej informacji na temat przełączników devenv, zobacz [przełączniki wiersza polecenia devenv](../ide/reference/devenv-command-line-switches.md) i [devenv przełączniki wiersza polecenia dla projektowania pakietu VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Aby uzyskać więcej informacji na temat sposobu rejestrowania pakietów dla przełączników wiersza polecenia, zobacz [Dodawanie przełączników wiersza polecenia](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Początkowy punkt wejścia  
 Plik Appenvstub.dll zawiera punkty wejścia do uzyskiwania dostępu do izolowanej powłoki. Gdy aplikacja zostanie uruchomiona, wywoła punkt początkowy wejścia Appenvstub.dll.  
  
 Zachowanie aplikacji można zmienić, zmieniając wartość ostatniego parametru, który jest przesyłany do początkowego punktu wejścia. Aby uzyskać więcej informacji, zobacz [izolowane punkty wejścia powłoki (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Polu. Plik vsct  
 Plik. vsct umożliwia określenie standardowych elementów interfejsu użytkownika programu Visual Studio, które są dostępne w aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Polu. Plik PKGUNDEF  
 Gdy aplikacja jest zainstalowana na komputerze, na którym jest już zainstalowany program Visual Studio, kopia wpisów rejestru programu Visual Studio jest wykonywana dla aplikacji. Domyślnie aplikacja używa pakietów VSPackage, które są już zainstalowane na komputerze. Plik. pkgundef umożliwia wykluczenie wpisów rejestru w celu usunięcia określonych elementów powłoki lub rozszerzeń programu Visual Studio z aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki PKGUNDEF](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Plik. pkgundef umożliwia wykluczenie wpisów rejestru w celu usunięcia określonych elementów powłoki lub rozszerzeń programu Visual Studio z aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki PKGUNDEF](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Zestaw identyfikatorów GUID pakietów, które można wykluczyć, znajduje się na liście [identyfikatorów GUID pakietu funkcji programu Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Polu. Plik pkgdef  
 Plik. pkgdef umożliwia zdefiniowanie wpisów rejestru dla aplikacji, które są ustawiane podczas instalowania aplikacji. Opis pliku. pkgdef oraz listę wpisów rejestru używanych przez program Visual Studio Shell można znaleźć w temacie [. Pliki pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Ciągi podstawienia  
 Ciągi podstawienia używane w plikach. pkgdef i. pkgundef są wymienione w [ciągach podstawienia używanych w programie. Pkgdef i. Pliki PKGUNDEF](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Inne ustawienia  
 Jeśli izolowana aplikacja powłoki jest zależna od Microsoft.VisualStudio.GraphModel.dll, należy dodać następujące powiązanie przekierowanie do pliku config aplikacji powłoki izolowanej:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
