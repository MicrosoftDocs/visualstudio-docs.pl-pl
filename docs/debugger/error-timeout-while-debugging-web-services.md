---
title: Błąd — Przekroczono limit czasu podczas debugowania usług sieci Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: efb77689c33d263723f146f9b2484748505406b6
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460276"
---
# <a name="error-timeout-while-debugging-web-services"></a>Błąd: przekroczono limit czasu podczas debugowania usług sieci Web
Gdy Pracujesz w usłudze sieci Web XML przy użyciu kodu wywołującego, wywołanie może czasami przekroczyć limit czasu, z wynikiem nie można kontynuować debugowania. Może zostać wyświetlony komunikat o błędzie, taki jak ten.

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>Rozwiązanie
 Aby uniknąć tego problemu, należy ustawić wartość limitu czasu dla wywołania usługi sieci Web XML na nieskończoność, jak pokazano w poniższym przykładzie:

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
