---
title: Ocena stosu wywołań | Dokumentacja firmy Microsoft
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
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3ab4877a1d6f772572f430c12c436ff5a4b8537
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772082"
---
# <a name="call-stack-evaluation"></a>Ocena stosu wywołań
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby wyświetlić ramki stosu stosu wywołań w trybie break, należy zaimplementować [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metody.  
  
## <a name="methods-for-evaluation"></a>Metody do oceny  
 Aparat debugowania prostego (DE) może być tylko jeden ramki stosu. Aby sprawdzić ramkę stosu w trybie break, musi implementować z następujących metod [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla ramki stosu. Kontekst kodu reprezentuje bieżący wskaźnik instrukcji w ramce stosu.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla ramki stosu. Kontekst dokumentu reprezentuje bieżącej lokalizacji w kodzie źródłowym dla ramki stosu. Wymagane w celu oglądania kodu źródłowego, które zostały zatrzymane w programie.|  
  
 Te metody wymagają wykonania kilku powiązanych z kontekstu interfejsy i metody. W związku z tym, należy zaimplementować [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) metody i z następujących metod [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku kontekstu dokumentu.|  
  
 Wyliczenie kontekstów kodu, musi implementować wszystkie metody [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)

