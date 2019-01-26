---
title: 'Błąd: Przekroczono limit czasu podczas debugowania usług sieci Web | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0963d1675c3456601aba70bb5291b7cc19d454fb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930761"
---
# <a name="error-timeout-while-debugging-web-services"></a>Błąd: Przekroczono limit czasu podczas debugowania usług sieci Web
Gdy są Wkraczanie do usługi sieci Web XML, z kodu wywołującego, wywołanie może czasami limit czasu, w wyniku możliwe, że nie można kontynuować debugowanie. Zobaczysz komunikat o błędzie, np. to.  
  
```cmd
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Rozwiązanie  
 Aby uniknąć tego problemu, należy ustawić wartość limitu czasu dla wywołania usługi sieci Web XML na wartość infinite, jak pokazano w poniższym przykładzie:  
  
```csharp
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
