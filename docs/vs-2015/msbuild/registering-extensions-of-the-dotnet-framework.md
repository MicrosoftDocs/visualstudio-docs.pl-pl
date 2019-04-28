---
title: Rejestrowanie rozszerzeń środowiska .NET Framework | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5963faa5acb72ab0c94ca6b346456d83276e361
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445231"
---
# <a name="registering-extensions-of-the-net-framework"></a>Rejestrowanie rozszerzeń środowiska .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można opracować zestaw, który rozszerza określonej wersji programu .NET Framework. Aby włączyć zestawu są wyświetlane w programie Visual Studio **Add References** okno dialogowe, należy dodać folder, który zawiera go do rejestru systemowego.  
  
 Na przykład załóżmy, że firma Trey Research przygotowała bibliotekę, która rozszerza programu .NET Framework 4 i chce zestawy bibliotek, które pojawią się w **Add References** okno dialogowe, jeśli projekt jest przeznaczony dla .NET Framework 4. Również założono, że zestawy są zestawów 32-bitowych uruchomiona na komputerze 32-bitowym lub 64-bitowych zestawów uruchomionego na komputerze 64-bitowych i że ma być zainstalowany w folderze C:\TreyResearch\Extensions4\.  
  
 Przy użyciu tego klucza, należy zarejestrować tego folderu: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Należy podać klucz to wartość domyślna: C:\TreyResearch\Extensions4.  
  
> [!NOTE]
> Numer kompilacji programu .NET Framework w wersji może się różnić.  
  
 Aby zarejestrować zestaw 32-bitowego na komputerze 64-bitowym, za pomocą węzła Wow6432, na przykład: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Zobacz też  
 [Integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
