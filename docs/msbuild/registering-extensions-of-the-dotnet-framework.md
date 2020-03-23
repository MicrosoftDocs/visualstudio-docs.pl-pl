---
title: Rejestrowanie rozszerzeń programu .NET Framework | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e7f79e04cc9afb4238c9f6292a99da684066a7d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632865"
---
# <a name="register-extensions-of-the-net-framework"></a>Rejestrowanie rozszerzeń programu .NET Framework

Można opracować zestaw, który rozszerza określoną wersję programu .NET Framework. Aby umożliwić zestaw do wyświetlenia w oknie dialogowym **Dodawanie odwołań** programu Visual Studio, należy dodać folder, który zawiera go do rejestru systemowego.

 Załóżmy na przykład, że firma Trey Research opracowała bibliotekę, która rozszerza program .NET Framework 4 i chce, aby zestawy biblioteki były wyświetlane w oknie dialogowym **Dodawanie odwołań,** gdy projekt jest przeznaczony dla programu .NET Framework 4. Należy również przyjąć, że zestawy są zestawami 32-bitowymi działającymi na komputerze 32-bitowym lub 64-bitowymi działającymi na komputerze 64-bitowym i że zostaną zainstalowane w folderze *C:\TreyResearch\Extensions4.\\ *

 Zarejestruj ten folder za pomocą tego klucza: **\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Nadaj kluczowi tę wartość domyślną: **C:\TreyResearch\Extensions4**.

> [!NOTE]
> Numer kompilacji wersji programu .NET Framework może być inny.

 Aby zarejestrować 32-bitowy zestaw na komputerze 64-bitowym, użyj węzła Wow6432, na przykład: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.

### <a name="see-also"></a>Zobacz też

- [Integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
