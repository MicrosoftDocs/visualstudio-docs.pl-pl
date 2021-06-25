---
title: Konteksty debugera | Microsoft Docs
description: 'Dowiedz się, jak Visual Studio debugowania działa w różnych kontekstach: kontekście kodu, kontekście dokumentacji lub pozycji oraz kontekście oceny wyrażeń.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5103561a420c3836f60a22790335522a83798966
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903674"
---
# <a name="debugger-contexts"></a>Konteksty debugera
Podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania aparat debugowania (DE) działa jednocześnie w kilku różnych kontekstach w następujący sposób:

- Kontekst kodu, który opisuje bieżącą lokalizację w strumieniu wykonywania programu.

- Kontekst lub pozycja dokumentacji, która opisuje bieżącą pozycję w dokumencie źródłowym.

- Kontekst oceny wyrażeń, który opisuje kontekst, w którym będzie odbywać się ocena wyrażeń.

## <a name="in-this-section"></a>W tej sekcji
 [Kontekst kodu](../../extensibility/debugger/code-context.md) Omawia kontekst kodu jako adres w strumieniu instrukcji programu w współczesnych architekturach czasu uruchamiania i językach nietradycyjnych, gdzie kod może nie być reprezentowany przez instrukcje, ale niektóre inne sposoby.

 [Położenie dokumentu](../../extensibility/debugger/document-position.md) Definiuje pozycję dokumentu w Visual Studio debugowania za pomocą abstrakcji pozycji w pliku źródłowym, tak jak jest to znane w ide.

 [Kontekst dokumentu](../../extensibility/debugger/document-context.md) Omówienie kontekstu dokumentu w Visual Studio debugowania w odniesieniu do pliku źródłowego. Omówiono również sposób mapowania kontekstu kodu na kontekst dokumentacji przez program obsługi symboli.

 [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md) Zawiera informacje na temat kontekstu oceny wyrażeń w Visual Studio. Na przykład kontekst oceny wyrażeń skojarzony z ramką stosu zapewnia kontekst do oceny zmiennych lokalnych, parametrów metody i składowych klasy.

## <a name="related-sections"></a>Powiązane sekcje
 [Pojęcia dotyczące debugowania](../../extensibility/debugger/debugger-concepts.md) Opisuje główne pojęcia dotyczące architektury debugowania.

 [Składniki debugowania](../../extensibility/debugger/debugger-components.md) Zawiera omówienie składników debugowania Visual Studio, w tym aparatu debugowania (DE), ewaluatora wyrażeń (EE) i programu obsługi symboli (SH).

 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.
