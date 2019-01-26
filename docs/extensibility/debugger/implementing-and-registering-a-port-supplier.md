---
title: Implementowanie i rejestrowanie dostawcy portu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e02c7e7ff030d2fd2bb9de86dfd1e7211f8de1f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946714"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementowanie i rejestrowanie dostawcy portu
Rolą dostawcy portu jest śledzenie i podać portów, które z kolei zarządzać procesami. Gdy port musi zostać utworzona, dostawcy portu jest uruchomiony, przy użyciu CoCreate o identyfikatorze GUID dostawcy portu (Menedżer debugowania sesji [SDM] użyje dostawcy portu, który użytkownik wybrał lub dostawcę, port określony przez system projektu). Następnie wywołuje SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) aby zobaczyć, czy żadnych portów może być dodany. Jeśli port mogą być dodawane, nowy port jest wymagany przez wywołanie [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) i przekazanie do niej [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) port, który opisuje. `AddPort` Zwraca nowy port, reprezentowane przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejsu.  
  
## <a name="discussion"></a>Dyskusja  
 Port jest tworzony przez dostawcę portu, który jest skojarzony z serwerem maszyny lub debugowania. Serwer wylicza jej dostawcy portów za pomocą[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) metoda i dostawcy portu wylicza jego portów za pomocą [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) metody.  
  
 Oprócz typowych rejestracji modelu COM dostawcy portu musi zarejestrować się za pomocą programu Visual Studio, umieszczając jego identyfikator klasy i nazwy w lokalizacjach określonego rejestru. Wywołana funkcja pomocnika debugowania zestawu SDK `SetMetric` obsługuje tej kwestii: jest wywoływana jeden raz dla każdego elementu, należy zarejestrować ten sposób:  
  
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
  
 Dostawcy portu wyrejestrowuje przez wywołanie metody `RemoveMetric` (inną funkcję pomocnika debugowania zestawu SDK) jeden raz dla każdego elementu, który został zarejestrowany ten sposób:  
  
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
>  [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` i `RemoveMetric` są statyczne funkcje zdefiniowane w *dbgmetric.h* i kompilowanych w *ad2de.lib*. `metrictypePortSupplier`, `metricCLSID`, I `metricName` pomocników również są zdefiniowane w *dbgmetric.h*.  
  
 Dostawcy portu można podać jego nazwę i identyfikator GUID za pomocą metody [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) i [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), odpowiednio.  
  
## <a name="see-also"></a>Zobacz także  
 [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)