---
title: Implementowanie i rejestrowanie dostawcy portu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430261"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementowanie i rejestrowanie dostawcy portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rolą dostawcy portu jest śledzenie i podać portów, które z kolei zarządzać procesami. W czasie, który port musi zostać utworzona dostawcy portu jest uruchomiony, przy użyciu CoCreate o identyfikatorze GUID dostawcy portu (Menedżer debugowania sesji [SDM] używane dostawcy portu wybranego użytkownika lub dostawcę port określony przez system projektu). Następnie wywoła SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) aby zobaczyć, czy żadnych portów może być dodany. Jeśli port mogą być dodawane, nowy port jest wymagany przez wywołanie [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) i przekazanie do niej [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) port, który opisuje. `AddPort` Zwraca nowy port, reprezentowane przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejsu.  
  
## <a name="discussion"></a>Dyskusja  
 Port jest tworzony przez dostawcę portu, który jest skojarzony z serwerem maszyny lub debugowania. Serwer można wyliczyć dostawców za pośrednictwem portu[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) metoda i dostawcy portu można wyliczyć jego portów za pomocą [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) metody.  
  
 Oprócz typowych rejestracji modelu COM dostawcy portu musi zarejestrować się za pomocą programu Visual Studio, umieszczając jego identyfikator klasy i nazwy w lokalizacjach określonego rejestru. Wywołana funkcja pomocnika debugowania zestawu SDK `SetMetric` obsługuje tej kwestii: jest wywoływana jeden raz dla każdego elementu, należy zarejestrować ten sposób:  
  
```cpp#  
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
  
```cpp#  
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
> [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` i `RemoveMetric` są statyczne funkcje zdefiniowane w dbgmetric.h i kompilowane do ad2de.lib. `metrictypePortSupplier`, `metricCLSID`, I `metricName` pomocników również są zdefiniowane w dbgmetric.h.  
  
 Dostawcy portu można podać jego nazwę i identyfikator GUID za pomocą metody [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) i [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
