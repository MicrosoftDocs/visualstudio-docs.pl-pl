---
title: Implementowanie i rejestrowanie dostawcy portu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3844d6beca76781f741bfbe0c6bff71923075d36
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728943"
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
>  [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` i `RemoveMetric` są statyczne funkcje zdefiniowane w dbgmetric.h i kompilowane do ad2de.lib. `metrictypePortSupplier`, `metricCLSID`, I `metricName` pomocników również są zdefiniowane w dbgmetric.h.  
  
 Dostawcy portu można podać jego nazwę i identyfikator GUID za pomocą metody [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) i [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)

