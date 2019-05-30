---
title: Konteksty debugera | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 011999929fd4cb1508bf4958629e622684f35739
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345996"
---
# <a name="debugger-contexts"></a>Konteksty debugera
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania, aparat debugowania (DE) działa jednocześnie w ramach kilku różnych kontekstach, w następujący sposób:

- Kontekst kodu w tym artykule opisano bieżącej lokalizacji w usłudze stream wykonywania programu.

- Dokumentacja kontekstu lub pozycji, który opisuje bieżącą pozycję w dokumencie źródłowym.

- Kontekst oceny wyrażeń, który opisuje kontekst, w wyrażeniu, które odbędzie się oceny.

## <a name="in-this-section"></a>W tej sekcji
 [Kontekst kodu](../../extensibility/debugger/code-context.md) Discusses kontekst kodu jako adresu program strumień instrukcji w współczesnych środowiska wykonawczego architektury i nietradycyjnych języków, gdzie kod nie może być reprezentowany przez instrukcje, ale w inny sposób.

 [Położenie dokumentu](../../extensibility/debugger/document-position.md) definiuje położenie dokumentu podczas debugowania programu Visual Studio za pomocą abstrakcję pozycji w pliku źródłowym, ponieważ wiadomo, że środowisko IDE.

 [Kontekst dokumentu](../../extensibility/debugger/document-context.md) Discusses jakie kontekstu dokumentu reprezentuje podczas debugowania programu Visual Studio w odniesieniu do pliku źródłowego. Omówiono również sposób obsługi symboli mapowania kontekst kodu do kontekstu dokumentacji.

 [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md) zawiera informacje na temat oceny wyrażenia kontekstu w programie Visual Studio. Na przykład oceny wyrażenia kontekstu skojarzonego z ramką stosu udostępnia kontekst dla ocenianie zmiennych lokalnych, parametrów metod i składowych klasy.

## <a name="related-sections"></a>Sekcje pokrewne
 [Debugowanie pojęcia](../../extensibility/debugger/debugger-concepts.md) opisano główne pojęcia dotyczące architektury debugowania.

 [Debugowanie składników](../../extensibility/debugger/debugger-components.md) zawiera omówienie składników, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH) debugowania programu Visual Studio.

 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md) zawiera łącza do różnych zadań debugowania, takich jak uruchamianie programu i wyrażeń.