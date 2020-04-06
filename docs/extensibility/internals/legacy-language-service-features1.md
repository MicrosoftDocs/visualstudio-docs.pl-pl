---
title: Starsze funkcje usługi językowej1 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707401"
---
# <a name="legacy-language-service-features"></a>Funkcje starszej wersji usługi językowej
Usługa języka struktury pakietów zarządzanych (MPF) może obsługiwać jedną lub więcej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcji, takich jak wyróżnianie składni, IntelliSense i sprawdzanie poprawności punktu przerwania. Każda funkcja może być zaimplementowana niezależnie od innych, ale wszystkie wymagają analizatora i skanera, z wyjątkiem wyróżniania składni, co wymaga tylko skanera.

## <a name="in-this-section"></a>W tej sekcji
- [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi dopasowania pary języków, znany również jako dopasowywanie nawiasów klamrowych.

- [Komentowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi komentowania i dekommentacji wybranego kodu.

- [Niestandardowe właściwości dokumentu w starszej wersji usługi językowej](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi właściwości dokumentu, które są osadzone w pliku źródłowym.

- [Zwijanie w starszej wersji usługi językowej](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi nakreślenia za pośrednictwem implementacji ukrytych regionów.

- [Ponowne formatowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi kodu formatowania.

- [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi fragmentów kodu, które są segmenty kodu, które są wstawiane i mogą być edytowane.

- [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 W tym artykule opisano, co jest wymagane do obsługi intellisense parametr info operacji wyświetlania podpisu metody, jak metoda jest wpisywany.

- [Szybkie informacje w starszej wersji usługi językowej](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi operacji IntelliSense Szybkie informacje do wyświetlania informacji o identyfikatorze.

- [Uzupełnianie składowych w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi intellisense element członkowski ukończenie operacji wyboru członka obszaru nazw z listy.

- [Uzupełnianie wyrazów w starszej wersji usługi językowej](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi intellisense complete word operacji ukończenia częściowo wpisane wyrazy.

- [Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Opisuje, co usługa języka może zrobić, aby obsługiwać okno **Autos** podczas debugowania.

- [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 W tym artykule opisano sposób korzystania z **paska nawigacyjnego** w górnej części widoku edytora, aby zapewnić szybką nawigację do dowolnego typu lub elementu członkowskiego w pliku wyświetlanym w tym widoku..

- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 W tym artykule opisano, co jest wymagane do obsługi wyróżniania składni kodu źródłowego.

- [Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 W tym artykule opisano, co usługa języka może zrobić do obsługi sprawdzania poprawności punktów przerwania poza debugerem.

## <a name="related-sections"></a>Sekcje pokrewne
- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 W tym artykule opisano analizatora i skanera, które są wymagane do zaimplementowania wszystkich funkcji usługi języka, która używa struktury pakietu zarządzanego.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 W tym artykule opisano, co jest wymagane do zaimplementowania usługi języka przy użyciu mpf.

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)

 W tym artykule opisano kroki, które są wymagane [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]do zarejestrowania usługi języka opartej na mpf w pliku .

- [Korzystanie z IntelliSense](../../ide/using-intellisense.md)

 W tym artykule wyjaśniono, w jaki sposób technologia IntelliSense ułatwia dostęp do odniesień do języków.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Zawiera informacje dotyczące sposobu korzystania z struktury pakietów zarządzanych (MPF) w celu zaimplementowania w pełni funkcjonej usługi języka w kodzie zarządzanym.
