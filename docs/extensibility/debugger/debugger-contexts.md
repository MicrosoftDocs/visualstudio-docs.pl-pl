---
title: Konteksty debugera | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738975"
---
# <a name="debugger-contexts"></a>Konteksty debugera
Podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania aparat debugowania (DE) działa jednocześnie w kilku różnych kontekstach, w następujący sposób:

- Kontekst kodu, który opisuje bieżącą lokalizację w strumieniu wykonywania programu.

- Kontekst dokumentacji lub stanowisko, które opisuje bieżące stanowisko w dokumencie źródłowym.

- Kontekst oceny wyrażenia, który opisuje kontekst, w którym będzie odbywać się ocena wyrażenia.

## <a name="in-this-section"></a>W tej sekcji
 [Kontekst kodu](../../extensibility/debugger/code-context.md) W tym artykule omówiono kontekst kodu jako adres w strumieniu instrukcji programu w dzisiejszych architekturach w czasie wykonywania w porównaniu do języków nietradycyjnych, gdzie kod może nie być reprezentowany przez instrukcje, ale niektóre inne środki.

 [Pozycja dokumentu](../../extensibility/debugger/document-position.md) Definiuje położenie dokumentu w programie Visual Studio debugowania za pomocą abstrakcji pozycji w pliku źródłowym, jak znany IDE.

 [Kontekst dokumentu](../../extensibility/debugger/document-context.md) W tym artykule omówiono kontekst dokumentu w debugowaniu programu Visual Studio w odniesieniu do pliku źródłowego. Również w tym artykule omówiono sposób, w jaki program obsługi symboli mapuje kontekst kodu do kontekstu dokumentacji.

 [Kontekst oceny wyrażenia](../../extensibility/debugger/expression-evaluation-context.md) Zawiera informacje na temat kontekstu oceny wyrażenia w programie Visual Studio. Na przykład kontekst oceny wyrażenia skojarzony z ramką stosu zapewnia kontekst do oceny zmiennych lokalnych, parametrów metody i elementów członkowskich klasy.

## <a name="related-sections"></a>Powiązane sekcje
 [Pojęcia debugowania](../../extensibility/debugger/debugger-concepts.md) W tym artykule opisano główne debugowanie koncepcji architektury.

 [Składniki debugowania](../../extensibility/debugger/debugger-components.md) Zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), oceniający wyrażenia (EE) i program obsługi symboli (SH).

 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) Zawiera łącza do różnych zadań debugowania, takich jak uruchamianie programu i oceny wyrażeń.
