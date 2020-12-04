---
title: Implementowanie i rejestrowanie dostawcy portów | Microsoft Docs
description: Dowiedz się, jak zaimplementować i zarejestrować dostawcę portów, który śledzi i dostarcza porty, które zarządzają procesami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5bce26a00a525ed93e27b531b36aca1fc04dce4
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559930"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementowanie i rejestrowanie dostawcy portu
Rolą dostawcy portów jest śledzenie i dostarczanie portów, które z kolei zarządzają procesami. Gdy należy utworzyć port, dostawca portu jest tworzony przy użyciu CoCreate z identyfikatorem GUID dostawcy portu (Menedżer debugowania sesji [SDM] będzie używał dostawcy portu wybranego przez użytkownika lub dostawcę portu określonego przez system projektu). Model SDM następnie wywołuje [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) , aby sprawdzić, czy można dodać dowolne porty. Jeśli można dodać port, żądanie nowego portu jest wymagane przez wywołanie funkcji [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) i przekazanie jej [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , która opisuje port. `AddPort` zwraca nowy port reprezentowany przez interfejs [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .

## <a name="discussion"></a>Dyskusja
 Port jest tworzony przez dostawcę portu, który jest skojarzony z maszyną lub serwerem debugowania. Serwer wylicza dostawców portów za pomocą metody[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) , a dostawca portu wylicza swoje porty za pomocą metody [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .

 Oprócz typowej rejestracji modelu COM dostawca portu musi się zarejestrować w programie Visual Studio, umieszczając jego identyfikator CLSID i nazwę w określonych lokalizacjach rejestru. Funkcja pomocnika zestawu SDK debugowania o nazwie `SetMetric` obsługuje te czynności: jest wywoływana jednokrotnie dla każdego elementu, który ma zostać zarejestrowany:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Dostawca portu wyrejestrowuje siebie `RemoveMetric` , wywołując (inną funkcję pomocnika SDK debugowania) jednokrotnie dla każdego zarejestrowanego elementu:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> [Pomocników zestawu SDK na potrzeby debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` i `RemoveMetric` są funkcjami statycznymi zdefiniowanymi w *dbgmetric. h* i skompilowanymi w *ad2de. lib*. `metrictypePortSupplier`, `metricCLSID` , I `metricName` pomocnicy są również zdefiniowane w *dbgmetric. h*.

 Dostawca portu może podać jego nazwę i identyfikator GUID odpowiednio do metod [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) i [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md).

## <a name="see-also"></a>Zobacz także
- [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Pomocnicy zestawu SDK na potrzeby debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
