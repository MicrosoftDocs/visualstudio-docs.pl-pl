---
title: Omówienie usługi starszego języka | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c48c146c38acf905b08ca756e69053dfd6aac28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040571"
---
# <a name="legacy-language-service-overview"></a>Omówienie starszej wersji usługi językowej
Usługa języka zapewnia pomoc techniczna do edytora, które umożliwia Implementowanie pewnych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcji. Klasy usługi języka zarządzanego pakietu Framework (MPF) zapewniają pełną obsługę dla najczęściej używanych funkcji i częściowa Obsługa innych funkcji.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Funkcje w pełni obsługiwana w MPF  
 Klasy usługi w języka MPF obsługuje następujące funkcje:  
  
-   Wyróżnianie składni  
  
-   Tworzenie konspektu  
  
-   Dodawanie komentarza do bloków kodu  
  
-   Parowanie nawiasów klamrowych  
  
-   Fragmenty kodu  
  
-   Niestandardowe właściwości dokumentu  
  
-   Informacje o parametrach funkcji IntelliSense  
  
-   Funkcja IntelliSense, szybkie informacje  
  
-   Uzupełnianie składowych funkcji IntelliSense  
  
-   Uzupełnianie wyrazów IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Częściowo obsługiwane funkcje w MPF  
 MPF zapewnia tylko częściowe obsługę następujących funkcji. Oznacza to, że musi implementować metody, które są wywoływane przez MPF.  
  
-   Automatyczne formatowanie kodu. Możesz podać kod, który implementuje, ponownego formatowania.  
  
-   Sprawdzanie poprawności punktów przerwania, określając prawidłowy kod zakresów. Możesz podać kod, który identyfikuje zakresy kodu.  
  
-   Obsługa debugera **Autos** okna do wyświetlania zmiennych. Możesz podać kod, który określa, co do wyświetlenia w oknie.  
  
-   Obsługa **pasek nawigacyjny** Szybkie nawigowanie między typów i elementów członkowskich. Implementowanie i zwracają klasy pomocnika, która wypełnia listy w **pasek nawigacyjny** pola kombi.  
  
## <a name="implementation"></a>Implementacja  
 Należy wykonać kilka kroków dotyczących implementacji samą usługę języka i funkcji usługi języka, które mają być obsługiwane dla danego języka. W poniższych tematach omówiono następujące kroki:  
  
-   [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Zwijanie w starszej wersji usługi językowej](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Komentowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Ponowne formatowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Niestandardowe właściwości dokumentu w starszej wersji usługi językowej](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Uzupełnianie wyrazów w starszej wersji usługi językowej](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Uzupełnianie składowych w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Szybkie informacje w starszej wersji usługi językowej](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Rozszerzalność starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md)