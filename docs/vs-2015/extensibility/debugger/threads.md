---
title: Wątki | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054589"
---
# <a name="threads"></a>Wątki
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pod względem architektury debugera **wątku**:  
  
- Jest podstawową jednostką obliczeń. Wątek sekwencyjnie wykonuje instrukcji w ramach pojedynczego wywołania stosu, przechodzenia z jednego kodu kontekstu do następnego.  
  
- Można zidentyfikować sam, jak i program go jest uruchomiona i można o nazwie, wstrzymana, a wznowione. Wątek również wyliczyć jego ramek stosu skojarzone oraz w niektórych warunkach mogą zostać przeniesione do innej ramki stosu. Podany kontekst ramkę stosu, wątek może zwrócić skojarzony wątek logiczne ewentualne. Wątek ma właściwości, takie jak liczba Wstrzymaj, mogą być wyświetlane w oknie wątki w IDE.  
  
- Jest reprezentowany przez [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)
