---
title: Rejestrowanie rozszerzeń .NET Framework | Microsoft Docs
description: Dowiedz się, jak dodać folder zawierający zestaw, który rozszerza określoną wersję .NET Framework do rejestru systemowego.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d63dda9cab50474fd357043d5f694a645a18b2b9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048756"
---
# <a name="register-extensions-of-the-net-framework"></a>Rejestrowanie rozszerzeń .NET Framework

Można opracować zestaw, który rozszerza określoną wersję .NET Framework. Aby włączyć zestaw, aby pojawił się w oknie dialogowym **Dodaj odwołania** programu Visual Studio, należy dodać folder zawierający go do rejestru systemowego.

 Załóżmy na przykład, że firma Trey Research opracowała bibliotekę, która rozszerza .NET Framework 4 i chce, aby zestawy bibliotek były wyświetlane w oknie dialogowym **Dodaj odwołania** , gdy projekt jest przeznaczony dla .NET Framework 4. Załóżmy również, że zestawy są 32-bitowe zestawy działające na komputerze 32-bitowym lub 64-bitowym, które działają na komputerze 64-bitowym, i że zostaną zainstalowane w *folderze \\ C:\TreyResearch\Extensions4* .

 Zarejestruj ten folder przy użyciu tego klucza: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\** . Nadaj kluczowi tę wartość domyślną: **C:\TreyResearch\Extensions4** .

> [!NOTE]
> Numer kompilacji .NET Framework może być różny.

 Aby zarejestrować zestaw 32-bitowy na komputerze 64-bitowym, Użyj węzła Wow6432, na przykład: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\** .

### <a name="see-also"></a>Zobacz też

- [integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
