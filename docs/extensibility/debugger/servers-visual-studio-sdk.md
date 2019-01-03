---
title: Serwery (zestaw SDK programu Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 109c24935511f98e5eb3b5d83270960e5a0c6855
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905562"
---
# <a name="servers-visual-studio-sdk"></a>Serwery (zestaw SDK programu Visual Studio)
W architekturze debugera *serwera*:  
  
-   Jest kontenerem portów i dostawcy portów i komunikuje się portów i dostawcy portów Menedżer debugowania sesji (SDM) i aparaty debugowania.  
  
-   Można zidentyfikować się według nazwy i wyliczanie jego portów i dostawcy portów.  
  
-   Jest reprezentowany przez [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfejs, który jest implementowane tylko przez program Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia uruchomienia programu Visual Studio).  
  
## <a name="see-also"></a>Zobacz także  
 [Porty](../../extensibility/debugger/ports.md)   
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)