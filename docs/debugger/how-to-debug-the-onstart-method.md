---
title: 'Instrukcje: Debugowanie metody OnStart | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 2bf37bef11c4d07ac0cb2c218f03f344a02ed4e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005571"
---
# <a name="how-to-debug-the-onstart-method"></a>Instrukcje: Debugowanie metody OnStart
Usługa Windows można debugować, uruchamiając usługi i dołączanie debugera do procesu usługi. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie aplikacji usług Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Jednak aby debugować <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> metody usługi Windows, można uruchomić debugera z wewnątrz metody.  
  
1.  Dodaj wywołanie do <xref:System.Diagnostics.Debugger.Launch%2A> na początku `OnStart()`metody.  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Uruchom usługę (możesz użyć `net start`, lub uruchomić go w **usług** okno).  
  
     Powinny pojawić się okno dialogowe podobne do następującego:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Wybierz **tak, debugowanie \<nazwa usługi >.**  
  
4.  W oknie debugera just in Time wybierz wersję programu Visual Studio, którego chcesz użyć do debugowania.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Nowe wystąpienie programu Visual Studio uruchomi się i wykonywania jest zatrzymywany w `Debugger.Launch()` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)