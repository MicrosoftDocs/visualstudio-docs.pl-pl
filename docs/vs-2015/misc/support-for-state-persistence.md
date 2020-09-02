---
title: Obsługa trwałości stanu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434322"
---
# <a name="support-for-state-persistence"></a>Obsługa trwałości stanu
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] może zachować stan wspólnych obiektów. Na przykład, rozwiązanie i właściwości projektu są zapisywane i przywracane z rozwiązań i plików projektów. Ustawienia użytkownika mogą zostać wyeksportowane do plików ustawień i zaimportowane z nich.  
  
 Pakietów VSPackage zazwyczaj polega na lokalnym magazynie w rejestrze systemowym lub w folderze dane aplikacji dla bieżącego użytkownika lub komputera. Wartości, które wymagają małej ilości miejsca na magazyn, takie jak liczby całkowite i ciągi, są zwykle przechowywane w rejestrze systemowym. Wartości wymagające dużej ilości miejsca na potrzeby magazynu, takie jak mapy bitowe, są zapisywane w pliku. Ścieżka pliku może zostać zapisana w rejestrze systemu. Mechanizm trwałości musi mieć uprawnienia dostępu do magazynu lokalnego.  
  
## <a name="support-for-locating-local-storage"></a>Obsługa lokalizowania magazynu lokalnego  
 <xref:Microsoft.VisualStudio.Shell.Package>Klasa zapewnia obsługę lokalizowania informacji o stanie w folderze systemowym rejestru lub danych aplikacji dla bieżącego użytkownika lub komputera.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Zwraca ścieżkę do katalogu głównego rejestru komputera lokalnego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , na przykład HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0Exp.  
  
 Katalog główny rejestru lokalnego jest uzyskiwany z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> usługi. Jeśli ta wartość jest niedostępna, jest uzyskiwana z <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> atrybutu pakietu VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Zwraca ścieżkę do katalogu głównego rejestru bieżącego użytkownika (na komputer) dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , na przykład HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0Exp.  
  
 Katalog główny rejestru lokalnego jest uzyskiwany z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> usługi. Jeśli ta wartość jest niedostępna, jest uzyskiwana z atrybutu DefaultLocalRegistryRoot pakietu VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Zwraca ścieżkę katalogu, który służy jako wspólne repozytorium [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] danych dla bieżącego użytkownika mobilnego, na przykład c:\Dokumenty i Settings \\ *YourAccountName*\Dane Data\Microsoft\VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Zwraca ścieżkę katalogu, który służy jako wspólne repozytorium [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] danych dla bieżącego użytkownika niemobilnego, na przykład c:\Dokumenty i Settings \\ *YourAccountName*\Ustawienia lokalne\Dane Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Zobacz też  
 [Stan pakietu VSPackage](../misc/vspackage-state.md)