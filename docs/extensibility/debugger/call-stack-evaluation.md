---
title: Ocena stosu wywołań | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa28460c2680a5301768c950eac39caefc5d1dae
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332470"
---
# <a name="call-stack-evaluation"></a>Ocena stosu wywołań
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

## <a name="see-also"></a>Zobacz także
- [Wykonanie kontroli i stan oceny](../../extensibility/debugger/execution-control-and-state-evaluation.md)