---
title: Omówienie starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się więcej na temat starszych usług językowych w programie Visual Studio i funkcji obsługiwanych przez klasy usługi języka Managed Package Framework (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 236fc2a2923ffd0829f74ab56a119ff81b29cd7f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061176"
---
# <a name="legacy-language-service-overview"></a>Omówienie starszej wersji usługi językowej
Usługa językowa zapewnia obsługę edytora, która umożliwia implementowanie niektórych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcji. Klasy usługi języka Managed Package Framework (MPF) zapewniają pełną obsługę często używanych funkcji i częściową obsługę innych funkcji.

## <a name="fully-supported-features-in-the-mpf"></a>W pełni obsługiwane funkcje w MPF
 Klasy usługi językowej MPF obsługują następujące funkcje:

- Podświetlanie składni

- Tworzenie konspektu

- Komentowanie bloków kodu

- Dopasowywanie nawiasów klamrowych

- Fragmenty kodu

- Niestandardowe właściwości dokumentu

- Informacje o parametrach IntelliSense

- Szybkie informacje funkcji IntelliSense

- Uzupełnienie elementu członkowskiego IntelliSense

- Uzupełnianie wyrazów IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Częściowo obsługiwane funkcje w MPF
 MPF zapewnia tylko częściową pomoc techniczną dla następujących funkcji. Oznacza to, że należy zaimplementować metody, które są wywoływane przez MPF.

- Ponowne formatowanie kodu. Należy podać kod, który implementuje ponowne formatowanie.

- Sprawdzanie poprawności punktów przerwania przez zidentyfikowanie prawidłowych zakresów kodu. Należy podać kod, który identyfikuje zakresy kodu.

- Obsługa okna debugera **autoodtwarzania** do wyświetlania zmiennych. Należy podać kod określający, co ma być wyświetlane w oknie.

- Obsługa **paska nawigacyjnego** w celu szybkiej nawigacji między typami i elementami członkowskimi. Zaimplementowanie i zwrócenie klasy pomocnika, która wypełnia listy w polach kombi na **pasku nawigacyjnym** .

## <a name="implementation"></a>Implementacja
 Należy wykonać kilka czynności w celu zaimplementowania samej usługi językowej i funkcji usługi językowej, które mają być obsługiwane w Twoim języku. Te kroki omówiono w następujących tematach:

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Zwijanie w starszej wersji usługi językowej](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Komentowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Ponowne formatowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Niestandardowe właściwości dokumentu w starszej wersji usługi językowej](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Uzupełnianie wyrazów w starszej wersji usługi językowej](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Uzupełnianie składowych w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Szybkie informacje w starszej wersji usługi językowej](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Zobacz też
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Rozszerzalność starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md)
