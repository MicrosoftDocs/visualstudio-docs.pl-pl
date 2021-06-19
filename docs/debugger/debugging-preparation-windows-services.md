---
title: Przygotowanie do debugowania usług systemu Windows | Microsoft Docs
description: Przygotuj do debugowania usług systemu Windows, które są programami uruchamianymi w tle w systemie Windows, w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 01448fcd477f5b17b78ad2b142b965f30798746b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387740"
---
# <a name="debugging-preparation-windows-services"></a>Przygotowanie debugowania: usługi systemu Windows
Usługa systemu Windows to program, który działa w tle w systemie Microsoft Windows. Przykłady obejmują usługi Telnet i usługi czas systemu Windows, która aktualizuje zegar widoczny na komputerze. Usługa systemu Windows nie może być uruchamiana z poziomu programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; musi działać w kontekście Menedżera sterowania usługami. Aby uzyskać więcej informacji, zobacz Creating Windows Services , Debugging Windows Service Applications , and Windows Service Applications (Tworzenie usług [systemu Windows,](/dotnet/framework/windows-services/how-to-create-windows-services)debugowanie aplikacji usług systemu [Windows)](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)i [Windows Service Applications (Aplikacje usług systemu Windows).](/dotnet/framework/windows-services/index)

## <a name="see-also"></a>Zobacz też
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji Visual Basic debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Porady: debugowanie metody OnStart](../debugger/how-to-debug-the-onstart-method.md)