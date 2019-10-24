---
title: 'Instrukcje: debugowanie metody OnStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 107ce6d5ca2b327d77fe588e1ac7ffda10a0a3a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733628"
---
# <a name="how-to-debug-the-onstart-method"></a>Porady: debugowanie metody OnStart
Można debugować usługę systemu Windows, uruchamiając usługę i dołączając debuger do procesu usługi. Aby uzyskać więcej informacji, zobacz [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Jednak aby debugować metodę <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> usługi systemu Windows, należy uruchomić debuger z wewnątrz metody.

1. Dodaj wywołanie do <xref:System.Diagnostics.Debugger.Launch%2A> na początku `OnStart()`method.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Uruchom usługę (możesz użyć `net start` lub uruchomić ją w oknie **usługi** ).

    Powinno zostać wyświetlone okno dialogowe podobne do następujących:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Wybierz opcję **tak, debuguj \<service nazw >.**

4. W oknie Debuger just in Time wybierz wersję programu Visual Studio, która ma być używana na potrzeby debugowania.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Zostanie uruchomione nowe wystąpienie programu Visual Studio, a wykonywanie zostało zatrzymane przy użyciu metody `Debugger.Launch()`.

## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
