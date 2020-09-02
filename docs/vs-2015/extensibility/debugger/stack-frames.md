---
title: Ramki stosu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423390"
---
# <a name="stack-frames"></a>Ramki stosu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W zakresie architektury debugera, **Ramka stosu**:  
  
- Jest abstrakcją stosu, który zapewnia kontekst wykonywania wątku. Wątek jest zawsze wykonywany w ramach funkcji. Ramka stosu przechowuje zmienne lokalne funkcji i argumenty. Aby debugować za pomocą programu Visual Studio, debugowany język lub środowisko musi obsługiwać ramki stosu.  
  
- Może zarówno identyfikować, jak i opisywanie, a także zwracać skojarzony wątek. Ramka stosu może również zwracać kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji, jak również skojarzone z nimi konteksty oceny dokumentacji i wyrażenia.  
  
- Ma właściwości opisujące nazwę, typ i wartość zmiennych lokalnych i argumentów, które są wyświetlane w różnych oknach debugowania IDE.  
  
- Jest reprezentowany przez interfejs [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , zwykle tworzony przez aparat debugowania (de) lub maszynę wirtualną w ramach wykonywania wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
