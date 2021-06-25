---
title: Ocena stosu wywołań | Microsoft Docs
description: Dowiedz się więcej na temat metody EnumFrameInfo i sposobu jej implementowania w celu wyświetlania ramek stosu stosu wywołań w trybie przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 059c42349c7f8e681709d69104cf65a6fc245206
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898542"
---
# <a name="call-stack-evaluation"></a>Ocena stosu wywołań
Aby wyświetlić ramki stosu stosu wywołań w trybie przerwania, należy zaimplementować [metodę EnumFrameInfo.](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="methods-for-evaluation"></a>Metody oceny
 W przypadku prostego aparatu debugowania (DE) może być tylko jedna ramka stosu. Aby zbadać ramkę stosu w trybie przerwania, należy zaimplementować następujące metody [IDebugStackFrame2.](../../extensibility/debugger/reference/idebugstackframe2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla ramki stosu. Kontekst kodu reprezentuje bieżący wskaźnik instrukcji w ramce stosu.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla ramki stosu. Kontekst dokumentu reprezentuje bieżącą lokalizację w kodzie źródłowym ramki stosu. Wymagane do wyświetlania kodu źródłowego po zatrzymaniu w programie.|

 Te metody wymagają implementacji kilku interfejsów i metod związanych z kontekstem. W związku z tym należy zaimplementować [metodę GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) i następujące metody [IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku kontekstu dokumentu.|

 Aby wyliczyć konteksty kodu, należy zaimplementować wszystkie metody [IEnumDebugCodeContexts2.](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
