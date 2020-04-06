---
title: Ocena stosu połączeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739181"
---
# <a name="call-stack-evaluation"></a>Ocena stosu wywołań
Aby wyświetlić ramki stosu stosu wywołań w trybie przerwania, należy zaimplementować [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metody.

## <a name="methods-for-evaluation"></a>Metody oceny
 W przypadku prostego aparatu debugowania (DE) może istnieć tylko jedna ramka stosu. Aby sprawdzić ramkę stosu podczas trybu przerwania, należy zaimplementować następujące metody [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Metoda|Opis|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla ramki stosu. Kontekst kodu reprezentuje bieżący wskaźnik instrukcji w ramce stosu.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla ramki stosu. Kontekst dokumentu reprezentuje bieżącą lokalizację w kodzie źródłowym ramki stosu. Wymagane do wyświetlania kodu źródłowego po zatrzymaniu w programie.|

 Metody te wymagają implementacji kilku interfejsów i metod związanych z kontekstem. W związku z tym należy zaimplementować [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) metody i następujące metody [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Metoda|Opis|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku kontekstu dokumentu.|

 Aby wyliczyć konteksty kodu, należy zaimplementować wszystkie metody [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
