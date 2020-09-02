---
title: Obliczanie stosu wywołań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15fecbc61fec8ba7aa62ca7d79cf11c56b7ce938
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146413"
---
# <a name="call-stack-evaluation"></a>Ocena stosu wywołań
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby wyświetlić ramki stosu wywołań w trybie przerwania, należy zaimplementować metodę [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## <a name="methods-for-evaluation"></a>Metody oceny  
 Dla prostego aparatu debugowania może istnieć tylko jedna ramka stosu. Aby przeanalizować ramkę stosu w trybie przerwania, należy zaimplementować następujące metody [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla ramki stosu. Kontekst kodu reprezentuje bieżący wskaźnik instrukcji w ramce stosu.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla ramki stosu. Kontekst dokumentu reprezentuje bieżącą lokalizację w kodzie źródłowym ramki stosu. Wymagane do wyświetlania kodu źródłowego po zatrzymaniu w programie.|  
  
 Te metody wymagają implementacji kilku interfejsów i metod związanych z kontekstem. W tym celu należy zaimplementować metodę [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) oraz następujące metody [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku dla kontekstu dokumentu.|  
  
 Aby wyliczyć konteksty kodu, należy zaimplementować wszystkie metody [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
