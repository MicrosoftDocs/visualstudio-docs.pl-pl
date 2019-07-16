---
title: Elementy programu Isolated Shell | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204605"
---
# <a name="elements-of-the-isolated-shell"></a>Elementy programu Shell (izolowanego)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmodyfikować ustawień rejestru, ustawienia środowiska wykonawczego i punkt wejścia aplikacji w Twojej aplikacji isolated shell i jego vsct, .pkgdef, and.pkgundef plików.  
  
## <a name="registry-settings"></a>Ustawienia rejestru  
 Pkgdef i pkgundef pliki należy zmodyfikować ustawienia rejestru dotyczące aplikacji isolated shell. Gdy aplikacja jest uruchomiona, ustawienia rejestru są zdefiniowane w następującej kolejności:  
  
 Gdy aplikacja jest uruchomiona, ustawienia rejestru są zdefiniowane w następującej kolejności:  
  
1. Utworzenie klucza rejestru dla aplikacji.  
  
2. Rejestr jest aktualizowany z pliku .pkgdef aplikacji, definiując określonego klucze i wpisy.  
  
3. Dla każdego pakietu, który jest częścią aplikacji rejestr jest aktualizowany z pliku .pkgdef tego pakietu. Każdy pakiet jest zdefiniowana w pliku .pkgdef aplikacji przez $RootKey$ \Packages\\{*vsPackageGuid*} klucza dla pakietu.  
  
4. Rejestr jest aktualizowany z AppEnvConfig.pkgdef i BaseConfig.pkgdef w *ścieżka instalacji programu Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform katalogu. Te pliki to część pakietu Visual Studio, a także częścią pakietu redystrybucyjnego programu Visual Studio Shell (tryb izolowany).  
  
5. Rejestr jest aktualizowany z pliku pkgundef aplikacji przez usunięcie określonego klucze i wpisy.  
  
## <a name="run-time-settings"></a>Ustawienia środowiska wykonawczego  
 Po uruchomieniu aplikacji isolated shell wywołuje punkt wejścia uruchamiania powłoki programu Visual Studio. Ustawienia aplikacji są definiowane podczas uruchamiania aplikacji, w następujący sposób:  
  
1. Visual Studio shell sprawdza rejest aplikacji określonych kluczy. Jeśli ustawienie klucza jest określony w wywołaniu do rozpoczęcia punktu wejścia, ta wartość zastępuje wartość, w rejestrze.  
  
2. Jeśli punkt wejścia ani rejestru parametr określa wartość ustawienia, a następnie zostanie użyta domyślna wartość dla ustawienia.  
  
   Gdy użytkownik uruchamia aplikację z poziomu wiersza polecenia, wszystkie przełączniki wiersza polecenia są przekazywane do powłoki programu Visual Studio, który traktuje je w taki sam sposób, który wykonuje Devenv. Aby uzyskać więcej informacji na temat parametrów Devenv zobacz [przełączników wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md) i [przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Aby uzyskać więcej informacji na temat sposobu pakietu rejestruje przełączniki wiersza polecenia, zobacz [Dodawanie przełączników wiersza polecenia](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Punkt wejścia Start  
 Plik Appenvstub.dll zawiera punkty wejścia do uzyskiwania dostępu do programu isolated shell. Po uruchomieniu aplikacji wywoływanych przez nią punktu wejścia Start Appenvstub.dll.  
  
 Sposób działania aplikacji można zmienić, zmieniając wartość ostatni parametr, który jest przekazywany do rozpoczęcia punktu wejścia. Aby uzyskać więcej informacji, zobacz [izolowane powłoki wpis punktu parametrów (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>. Pliku Vsct  
 Pliku vsct pozwala określić, które standardowe elementy interfejsu użytkownika usługi Visual Studio są dostępne w aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>. Pliku Pkgundef  
 Aplikacja jest zainstalowana na komputerze, na którym jest już zainstalowany program Visual Studio, kopię wpisów rejestru programu Visual Studio są tworzone dla aplikacji. Domyślnie aplikacja używa pakietów VSPackage, które są już zainstalowane na komputerze. Pliku pkgundef pozwala wykluczyć wpisy rejestru w celu usuwania określonych elementów powłoki programu Visual Studio lub rozszerzenia z aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Pliku pkgundef pozwala wykluczyć wpisy rejestru w celu usuwania określonych elementów powłoki programu Visual Studio lub rozszerzenia z aplikacji. Aby uzyskać więcej informacji, zobacz [. Pliki Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Zestaw pakietów identyfikatory GUID, które można wykluczyć są wymienione w [identyfikatorów GUID programu Visual Studio funkcje pakietu](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>. Pliku Pkgdef  
 Plik .pkgdef pozwala zdefiniować wpisy rejestru dla aplikacji, które są ustawione, gdy aplikacja zostanie zainstalowana. Opis pliku .pkgdef i listy wpisów rejestru, który korzysta z powłoki programu Visual Studio, zobacz [. Pliki Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Ciągi podstawienia  
 Ciągi podstawienia używane w plikach pkgdef i pkgundef są wymienione w [podstawienia ciągi używane w. Pkgdef i. Pliki Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Inne ustawienia  
 Usługi aplikacji isolated shell jest zależna od Microsoft.VisualStudio.GraphModel.dll, należy dodać następujące przekierowanie powiązania do pliku config aplikacji Isolated Shell:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
