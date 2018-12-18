---
title: Port dostawców | Dokumentacja firmy Microsoft
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
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8ca5c7d9154b07cbc51b5fde6b9c85e97d880df
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751578"
---
# <a name="port-suppliers"></a>Dostawcy portów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pod względem architektury debugera **dostawcy portu**:  
  
- Znajduje się na serwerze i udostępnia porty na żądanie do tego serwera.  
  
- Dodawać i usuwać portów z zawierającego serwera.  
  
- Można wyliczyć wszystkie porty, które udostępnił się do serwera.  
  
- Jest reprezentowany przez [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu, który jest zarejestrowany w programie Visual Studio za pomocą rejestru. Ten interfejs można uzyskać przez wywołanie metody [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zapewnia dostawcy portu domyślnego i domyślny port. Jeśli port niestandardowy, musi zostać wdrożone, dostawca niestandardowy port również musi zaimplementować tak, aby podać te porty niestandardowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porty](../../extensibility/debugger/ports.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

