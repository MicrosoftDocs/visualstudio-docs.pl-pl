---
title: Ramek stosu | Dokumentacja firmy Microsoft
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
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebd9f1881f0e0579a3b319f6608cdbf348ed027b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789333"
---
# <a name="stack-frames"></a>Ramki stosu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pod względem architektury debugera **ramki stosu**:  
  
-   Jest klasą abstrakcyjną stosu, które dostarcza kontekst wykonanie wątku. Wątek jest zawsze wykonywane w ramach funkcji. Ramka stosu zawiera zmienne lokalne, funkcji i argumenty do niego. Aby debugować za pomocą programu Visual Studio, języka lub środowiska debugowania musi obsługiwać ramki stosu.  
  
-   Można zarówno zidentyfikować opisania siebie i może zwrócić skojarzonego wątku. Ramka stosu może również zwracać kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji, jak również skojarzony dokumentacji i konteksty oceny wyrażenia.  
  
-   Ma właściwości, które opisują nazwy, typu i wartości zmiennych lokalnych i argumenty, i które znajdują się w różnych oknach debugowania środowiska IDE.  
  
-   Jest reprezentowany przez [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

