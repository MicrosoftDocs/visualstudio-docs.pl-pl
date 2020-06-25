---
title: Jak debugować metodę OnStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7392b4185def34f38f0e183f2626bd648bb4b4ea
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350020"
---
# <a name="how-to-debug-the-onstart-method"></a>Porady: debugowanie metody OnStart
Można debugować usługę systemu Windows, uruchamiając usługę i dołączając debuger do procesu usługi. Aby uzyskać więcej informacji, zobacz [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Jednak aby debugować <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> metodę usługi systemu Windows, należy uruchomić debuger z wewnątrz metody.

1. Dodaj wywołanie do <xref:System.Diagnostics.Debugger.Launch%2A> początku `OnStart()` metody.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Uruchom usługę (możesz użyć programu `net start` lub uruchomić ją w oknie **usługi** ).

    Powinno zostać wyświetlone okno dialogowe podobne do następujących:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Wybierz opcję **tak, Debuguj \<service name> .**

4. W oknie Debuger just in Time wybierz wersję programu Visual Studio, która ma być używana na potrzeby debugowania.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Zostanie uruchomione nowe wystąpienie programu Visual Studio, a wykonywanie zostało zatrzymane w tej `Debugger.Launch()` metodzie.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
