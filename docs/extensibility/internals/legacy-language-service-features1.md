---
title: Starsza wersja usługi językowej Features1 | Microsoft Docs
description: Dowiedz się więcej na temat funkcji programu Visual Studio, które są obsługiwane w usłudze języka Managed Package Framework (MPF).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6e099798ff5fcc96e798742b16ba88e522a4bc0b
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205063"
---
# <a name="legacy-language-service-features-1"></a>Funkcje starszej wersji usługi językowej 1
Usługa języka Managed Package Framework (MPF) może obsługiwać jedną lub więcej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcji, takich jak wyróżnianie składni, IntelliSense i walidacja punktu przerwania. Każdą funkcję można zaimplementować niezależnie od innych, ale wszystkie wymagają analizatora i skanera, z wyjątkiem wyróżniania składni, które wymaga tylko skanera.

## <a name="in-this-section"></a>W tej sekcji
- [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi dopasowywania par języków, znanego również jako nawiasy klamrowe.

- [Komentowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi komentowania i usuwania komentarzy w wybranym kodzie.

- [Niestandardowe właściwości dokumentu w starszej wersji usługi językowej](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi właściwości dokumentu, które są osadzone w pliku źródłowym.

- [Zwijanie w starszej wersji usługi językowej](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi konspektu przez implementację ukrytych regionów.

- [Ponowne formatowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi ponownego formatowania kodu.

- [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi fragmentów kodu, które są segmentami kodu, które są wstawiane i mogą być edytowane.

- [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Opisuje, co jest wymagane do obsługi operacji informacji o parametrach IntelliSense na potrzeby wyświetlania sygnatury metody podczas wpisywania metody.

- [Szybkie informacje w starszej wersji usługi językowej](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi operacji szybkiej informacji funkcji IntelliSense do wyświetlania informacji o identyfikatorze.

- [Uzupełnianie składowych w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi operacji uzupełniania elementu członkowskiego IntelliSense na potrzeby wybierania elementu członkowskiego z listy.

- [Uzupełnianie wyrazów w starszej wersji usługi językowej](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Zawiera opis czynności, które należy spełnić, aby obsłużyć Kończenie operacji IntelliSense w programie Word na potrzeby uzupełniania wyrazów częściowo wpisanych.

- [Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Opisuje, co usługa języka może zrobić, aby obsłużyć okno **Autostarty** podczas debugowania.

- [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Opisuje sposób używania **paska nawigacyjnego** w górnej części widoku edytora w celu zapewnienia szybkiej nawigacji do dowolnego typu lub elementu członkowskiego w pliku pokazanym w tym widoku.

- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Opisuje, co jest wymagane do obsługi wyróżniania składni kodu źródłowego.

- [Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Opisuje, co usługa języka może zrobić, aby zapewnić obsługę walidacji punktów przerwania poza debugerem.

## <a name="related-sections"></a>Sekcje pokrewne
- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Opisuje Analizator i skaner, które są wymagane do zaimplementowania wszystkich funkcji usługi językowej, która używa zarządzanej struktury pakietów.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Opisuje, co jest wymagane do zaimplementowania usługi językowej przy użyciu MPF.

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Zawiera opis czynności, które są wymagane do zarejestrowania usługi językowej opartej na MPF [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)

 Wyjaśnia, w jaki sposób technologia IntelliSense ułatwia dostęp do języka.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Zawiera informacje dotyczące sposobu korzystania z struktury pakietu zarządzanego (MPF) w celu zaimplementowania w pełni funkcjonalnej usługi językowej w kodzie zarządzanym.
