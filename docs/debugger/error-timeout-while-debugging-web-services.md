---
title: Przekroczono limit czasu podczas debugowania usług sieci Web | Microsoft Docs
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
ms.openlocfilehash: 7f3522b61c8d7d78a182036d3a1f66c0495f5081
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852449"
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

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
