---
title: Konteksty debugera | Microsoft Docs
description: 'Dowiedz się, jak aparat debugowania programu Visual Studio działa w ramach odrębnych kontekstów: kontekstu kodu, kontekstu dokumentacji lub pozycji oraz kontekstu oceny wyrażenia.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89d2da35fb7ffa81ec9f6a882e6b35d42fc8f00c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952437"
---
# <a name="debugger-contexts"></a>Konteksty debugera
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowaniu aparat debugowania (de) działa jednocześnie w kilku odrębnych kontekstach w następujący sposób:

- Kontekst kodu, który opisuje bieżącą lokalizację w strumieniu wykonywania programu.

- Kontekst lub pozycja dokumentacji, która opisuje bieżące położenie w dokumencie źródłowym.

- Kontekst oceny wyrażenia, który opisuje kontekst, w którym będą wykonywane obliczenia wyrażeń.

## <a name="in-this-section"></a>W tej sekcji
 [Kontekst kodu](../../extensibility/debugger/code-context.md) Omawia kontekst kodu jako adres w strumieniu instrukcji programu w dzisiejszych architekturach czasu wykonywania i nietradycyjnych językach, gdzie kod nie może być reprezentowany przez instrukcje, ale inne sposoby.

 [Położenie dokumentu](../../extensibility/debugger/document-position.md) Definiuje położenie dokumentu w debugowaniu w programie Visual Studio za pomocą abstrakcji pozycji w pliku źródłowym, jak znany IDE.

 [Kontekst dokumentu](../../extensibility/debugger/document-context.md) Omówienie kontekstu dokumentu reprezentowanego w debugowaniu programu Visual Studio w odniesieniu do pliku źródłowego. Omówiono również sposób mapowania kontekstu kodu do kontekstu dokumentacji przez program obsługi symboli.

 [Kontekst oceny wyrażenia](../../extensibility/debugger/expression-evaluation-context.md) Zawiera informacje o kontekście oceny wyrażenia w programie Visual Studio. Na przykład kontekst oceny wyrażenia skojarzonego z ramką stosu zawiera kontekst do oceny zmiennych lokalnych, parametrów metody i elementów członkowskich klasy.

## <a name="related-sections"></a>Sekcje pokrewne
 [Koncepcje debugowania](../../extensibility/debugger/debugger-concepts.md) Opisuje główne koncepcje dotyczące architektury debugowania.

 [Debuguj składniki](../../extensibility/debugger/debugger-components.md) Zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), ewaluatora wyrażeń (EE) i obsługę symboli (SH).

 [Debuguj zadania](../../extensibility/debugger/debugging-tasks.md) Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.
