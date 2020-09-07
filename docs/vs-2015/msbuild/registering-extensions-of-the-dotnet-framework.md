---
title: Rejestrowanie rozszerzeń .NET Framework | Microsoft Docs
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
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "64831487"
---
# <a name="registering-extensions-of-the-net-framework"></a>Rejestrowanie rozszerzeń środowiska .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można opracować zestaw, który rozszerza określoną wersję .NET Framework. Aby włączyć zestaw, aby pojawił się w oknie dialogowym **Dodaj odwołania** programu Visual Studio, należy dodać folder zawierający go do rejestru systemowego.  
  
 Załóżmy na przykład, że firma Trey Research opracowała bibliotekę, która rozszerza .NET Framework 4 i chce, aby zestawy bibliotek były wyświetlane w oknie dialogowym **Dodaj odwołania** , gdy projekt jest przeznaczony dla .NET Framework 4. Załóżmy również, że zestawy są 32-bitowe zestawy działające na komputerze 32-bitowym lub 64-bitowym, które działają na komputerze 64-bitowym, i że zostaną zainstalowane w folderze C:\TreyResearch\Extensions4\.  
  
 Zarejestruj ten folder przy użyciu tego klucza: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\ . Nadaj kluczowi tę wartość domyślną: C:\TreyResearch\Extensions4.  
  
> [!NOTE]
> Numer kompilacji .NET Framework może być różny.  
  
 Aby zarejestrować zestaw 32-bitowy na komputerze 64-bitowym, Użyj węzła Wow6432, na przykład: HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\ .  
  
## <a name="see-also"></a>Zobacz też  
 [Integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
