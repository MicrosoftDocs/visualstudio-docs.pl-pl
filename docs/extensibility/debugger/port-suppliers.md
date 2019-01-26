---
title: Port dostawców | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf81cfeea10a0687e84982db595a5c7a9aab6074
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998225"
---
# <a name="port-suppliers"></a>Dostawcy portów
W architekturze debugera *dostawcy portu*:  
  
- Znajduje się na serwerze i udostępnia porty na żądanie do tego serwera.  
  
- Dodawać i usuwać portów z zawierającego serwera.  
  
- Można wyliczyć wszystkie porty, które udostępnił się do serwera.  
  
- Jest reprezentowany przez [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu, który jest zarejestrowany w programie Visual Studio za pomocą rejestru. Ten interfejs można uzyskać przez wywołanie metody [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia dostawcy portu domyślnego i domyślny port. Jeśli port niestandardowy, musi zostać wdrożone, dostawca niestandardowy port również musi zaimplementować tak, aby podać te porty niestandardowe.  
  
## <a name="see-also"></a>Zobacz także  
 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porty](../../extensibility/debugger/ports.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)