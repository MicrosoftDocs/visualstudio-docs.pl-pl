---
title: Przegląd usługi języka starszego | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707357"
---
# <a name="legacy-language-service-overview"></a>Omówienie starszej wersji usługi językowej
Usługa języka zapewnia obsługę edytora, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] która umożliwia implementowanie niektórych funkcji. Klasy usługi języka managed package framework (MPF) zapewniają pełną obsługę często używanych funkcji i częściową obsługę innych funkcji.

## <a name="fully-supported-features-in-the-mpf"></a>W pełni obsługiwane funkcje w mpf
 Klasy usługi języka MPF obsługują następujące funkcje:

- Wyróżnianie składni

- Tworzenie konspektu

- Komentowanie bloków kodu

- Dopasowywanie nawiasów klamrowych

- Fragmenty kodu

- Niestandardowe właściwości dokumentu

- Informacje o parametrach IntelliSense

- Szybkie informacje intellisense

- Ukończenie członkostwa w uszczynakłam IntelliSense

- Zakończenie słowa IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Częściowo obsługiwane funkcje w mpf
 MPF zapewnia tylko częściową obsługę następujących funkcji. Oznacza to, że należy zaimplementować metody, które są wywoływane przez MPF.

- Kod do formatowania. Podać kod, który implementuje formatowanie.

- Sprawdzanie poprawności punktów przerwania przez identyfikowanie prawidłowych zakresów kodu. Podać kod, który identyfikuje zakresy kodu.

- Obsługa okna **Autos** debugera do wyświetlania zmiennych. Podać kod, który określa, co ma być wyświetlane w oknie.

- Obsługa **paska nawigacyjnego** do szybkiej nawigacji między typami i członkami. Implementujesz i zwracasz klasę pomocnika, która wypełnia listy w polach kombi **paska nawigacyjnego.**

## <a name="implementation"></a>Wdrażanie
 Należy wykonać kilka kroków, aby zaimplementować samą usługę języka i funkcje usługi języka, które mają być obsługiwane dla języka. Te kroki są omówione w następujących tematach:

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
