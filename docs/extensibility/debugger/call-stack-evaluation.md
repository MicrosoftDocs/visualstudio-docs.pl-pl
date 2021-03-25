---
title: Obliczanie stosu wywołań | Microsoft Docs
description: Dowiedz się więcej o metodzie EnumFrameInfo i sposobach ich implementacji, aby wyświetlić ramki stosu wywołań w trybie przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c7e7180301965e43e6757340019c3506fe1a5e1f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055092"
---
# <a name="call-stack-evaluation"></a>Obliczanie stosu wywołań
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
- [Kontrola wykonywania i Ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
