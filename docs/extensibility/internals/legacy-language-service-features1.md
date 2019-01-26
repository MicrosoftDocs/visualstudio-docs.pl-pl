---
title: Starszej wersji usługi językowej1 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adb5e4dd96037eafa2b4e90f03f79dc2ec7f3b2b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031581"
---
# <a name="legacy-language-service-features"></a>Funkcje usługi starszego języka
Usługa języka zarządzanego pakietu framework (MPF) może obsługiwać co najmniej jeden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcji, takich jak wyróżnianie składni, funkcję IntelliSense i weryfikacji punktu przerwania. Poszczególne funkcje można zaimplementować niezależna od innych, ale wymaga analizator i skaner z wyjątkiem wyróżniania składni, która wymaga tylko skaner.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi języka pary dopasowanie, znany także jako parowanie nawiasów klamrowych.  
  
 [Komentowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi komentowania i Trwa usuwanie komentarza do zaznaczonego kodu.  
  
 [Niestandardowe właściwości dokumentu w starszej wersji usługi językowej](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi właściwości dokumentu, które są osadzone w pliku źródłowym.  
  
 [Zwijanie w starszej wersji usługi językowej](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi konspekt poprzez wdrożenie ukrytych regionów.  
  
 [Ponowne formatowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi formatowania kodu.  
  
 [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi fragmentów kodu, które segmenty kodu, które są wstawiane i można go edytować.  
  
 [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 W tym artykule opisano, co jest wymagane do obsługi operacji o parametrach funkcji IntelliSense do wyświetlania podpis metody jako metodę został wpisany.  
  
 [Szybkie informacje w starszej wersji usługi językowej](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi operacji szybkie informacje technologii IntelliSense, aby wyświetlić informacje dotyczące identyfikatora.  
  
 [Uzupełnianie składowych w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi operacji uzupełnianie składowych IntelliSense służąca do wybierania elementu członkowskiego w przestrzeni nazw z listy.  
  
 [Uzupełnianie wyrazów w starszej wersji usługi językowej](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi operacji IntelliSense, dokańczanie słów ukończenia częściowo wpisywanych słów.  
  
 [Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 W tym artykule opisano, co usługa języka zrobić, aby obsługiwać **Autos** okna podczas debugowania.  
  
 [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Opisuje sposób używania **pasek nawigacyjny** w górnej części widoku edytora, aby zapewnić szybką nawigację do dowolnego typu lub elementu członkowskiego w pliku, w tym widoku...  
  
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi, wyróżnianie składni kodu źródłowego.  
  
 [Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 W tym artykule opisano, co usługa języka zrobić, aby obsługiwać sprawdzanie poprawności punktów przerwania poza debugera.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 W tym artykule opisano analizator i skaner, które są wymagane do wykonania wszystkich funkcji wersji usługi językowej, która używa środowiska pakietu zarządzanego.  
  
 [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 W tym artykule opisano, co jest wymagane do wdrożenia usługi językowej przy użyciu MPF.  
  
 [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 W tym artykule opisano kroki, które są wymagane do zarejestrowania usługi języka opartego na MPF z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)  
 W tym artykule wyjaśniono, jak technologia IntelliSense sprawia, że informacje dotyczące języka łatwy dostęp do.  
  
 [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Zawiera informacje o tym, jak wdrożyć usługę w pełni funkcjonalne języka w kodzie zarządzanym przy użyciu środowiska pakietu zarządzanego (MPF).