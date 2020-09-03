---
title: Serwery (Visual Studio SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ed2ce924b22827a82a67664e3e473f0930a87e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199397"
---
# <a name="servers-visual-studio-sdk"></a>Serwery (zestaw SDK programu Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W zakresie architektury debugera, **serwera**:  
  
- Jest kontenerem portów i dostawców portów i służy do przekazywania portów i dostawców portów do Menedżera debugowania sesji (SDM) i aparatów debugowania.  
  
- Może identyfikować siebie według nazwy i wyliczać jej porty i dostawców portów.  
  
- Jest reprezentowany przez interfejs [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , który jest implementowany tylko przez program Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia programu Visual Studio uruchomionego).  
  
## <a name="see-also"></a>Zobacz też  
 [Np](../../extensibility/debugger/ports.md)   
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
