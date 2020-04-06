---
title: Wdrażanie i rejestracja dostawcy portu | Dokumenty firmy Microsoft
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
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738533"
---
# <a name="implement-and-register-a-port-supplier"></a>Wdrażanie i rejestrowanie dostawcy portu
Rolą dostawcy portu jest śledzenie i dostarczanie portów, które z kolei zarządzają procesami. Gdy port musi zostać utworzony, dostawca portu jest tworzony przy użyciu coCreate z identyfikatorem GUID dostawcy portu (menedżer debugowania sesji [SDM] użyje dostawcy portu wybranego przez użytkownika lub dostawcy portu określonego przez system projektu). Następnie SDM wywołuje [CanAddPort,](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) aby sprawdzić, czy można dodać jakieś porty. Jeśli można dodać port, nowy port jest wymagany przez wywołanie [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) i przekazanie go [IDebugPortRequest2,](../../extensibility/debugger/reference/idebugportrequest2.md) który opisuje port. `AddPort`zwraca nowy port reprezentowany przez interfejs [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md)

## <a name="discussion"></a>Dyskusji
 Port jest tworzony przez dostawcę portu, który jest skojarzony z serwerem komputera lub debugowania. Serwer wylicza swoich dostawców portów za pomocą[Metody EnumPortSuppliers,](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) a dostawca portu wylicza swoje porty za pomocą metody [EnumPorts.](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

 Oprócz typowej rejestracji COM dostawca portu musi zarejestrować się w programie Visual Studio, umieszczając jego identyfikator CLSID i nazwę w określonych lokalizacjach rejestru. Funkcja pomocnika debugowania SDK `SetMetric` o nazwie obsługuje ten chore: jest wywoływana raz dla każdego elementu, które mają być zarejestrowane, w związku z tym:

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

 Dostawca portu wyrejestrowuje `RemoveMetric` się, wywołując (inną funkcję pomocnika debugowania SDK) raz dla każdego elementu, który został zarejestrowany, w związku z czym:

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
> [Pomocników SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` i `RemoveMetric` są funkcje statyczne zdefiniowane w *dbgmetric.h* i skompilowany w *ad2de.lib*. `metricCLSID`W `metrictypePortSupplier`pliku `metricName` *dbgmetric.h*zdefiniowano również program , i pomocników.

 Dostawca portu może podać swoją nazwę i identyfikator GUID za pomocą metod [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) i [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), odpowiednio.

## <a name="see-also"></a>Zobacz też
- [Wdrażanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Pomocnicy SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
