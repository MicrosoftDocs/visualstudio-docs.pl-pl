---
title: Implementowanie i rejestrowanie dostawcy portów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824669"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementowanie i rejestrowanie dostawcy portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rolą dostawcy portów jest śledzenie i dostarczanie portów, które z kolei zarządzają procesami. W chwili, gdy port musi zostać utworzony, dostawca portu zostanie skonkretyzowany przy użyciu CoCreate z identyfikatorem GUID dostawcy portu (Menedżer debugowania sesji [SDM] będzie używać dostawcy portów wybranego przez użytkownika lub dostawcy portu określonego przez system projektu). Model SDM następnie wywoła [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) , aby sprawdzić, czy można dodać dowolne porty. Jeśli można dodać port, żądanie nowego portu jest wymagane przez wywołanie funkcji [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) i przekazanie jej [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , która opisuje port. `AddPort` zwróci nowy port reprezentowany przez interfejs [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## <a name="discussion"></a>Dyskusja  
 Port jest tworzony przez dostawcę portu, który jest z kolei skojarzony z maszyną lub serwerem debugowania. Serwer może wyliczyć swoich dostawców portów za pomocą metody[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) , a dostawca portu może wyliczyć swoje porty za pomocą metody [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 Oprócz typowej rejestracji modelu COM dostawca portu musi się zarejestrować w programie Visual Studio, umieszczając jego identyfikator CLSID i nazwę w określonych lokalizacjach rejestru. Funkcja pomocnika zestawu SDK debugowania o nazwie `SetMetric` obsługuje te czynności: jest wywoływana jednokrotnie dla każdego elementu, który ma zostać zarejestrowany:  
  
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
  
 Dostawca portu wyrejestrowuje siebie `RemoveMetric` , wywołując (inną funkcję pomocnika SDK debugowania) jednokrotnie dla każdego zarejestrowanego elementu:  
  
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
> [Pomocników zestawu SDK na potrzeby debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` i `RemoveMetric` są funkcjami statycznymi zdefiniowanymi w dbgmetric. h i skompilowanymi w ad2de. lib. `metrictypePortSupplier`, `metricCLSID` , I `metricName` pomocnicy są również zdefiniowane w dbgmetric. h.  
  
 Dostawca portu może podać jego nazwę i identyfikator GUID odpowiednio do metod [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) i [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Pomocnicy zestawu SDK na potrzeby debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
