---
title: Przygotowanie do debugowania usług systemu Windows | Microsoft Docs
description: Przygotuj się do debugowania usług systemu Windows, które są programami uruchamianymi w tle w systemie Windows w programie Visual Studio.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: bdf82b708440cb3201c5d05bd936c7f7d9c30729
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872396"
---
# <a name="debugging-preparation-windows-services"></a>Przygotowanie debugowania: usługi systemu Windows
Usługa systemu Windows to program uruchomiony w tle w systemie Microsoft Windows. Przykładami mogą być usługa Telnet i usługa czas systemu Windows, która aktualizuje zegar widoczny dla komputera. Nie można uruchomić usługi systemu Windows z poziomu programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; musi ona działać w kontekście menedżera kontroli usług. Aby uzyskać więcej informacji, zobacz [Tworzenie usług systemu Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [debugowanie aplikacji usług systemu Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)i [aplikacji usług systemu Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Zobacz też
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Porady: debugowanie metody OnStart](../debugger/how-to-debug-the-onstart-method.md)