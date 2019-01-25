---
title: Analizowanie i modelowanie architektury | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-devops-techdebt
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0caade57f2105ac387792cf98c3f7a74a8d935f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795463"
---
# <a name="analyze-and-model-your-architecture"></a>Analizowanie i modelowanie architektury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upewnij się, że Twoja aplikacja spełnia wymagania użytkowników przy użyciu architektury programu Visual Studio i modelowanie narzędzi do zaprojektowania i modelu aplikacji. Łatwiej zrozumieć istniejący kod programu za pomocą programu Visual Studio wizualizować strukturę kodu, zachowanie i relacje.  
  
 Twórz modele na różnych poziomach szczegółowości w całym cyklu życia aplikacji w ramach procesu tworzenia aplikacji. Śledzenie wymagań, zadań, przypadków testowych, usterek i innych zadań skojarzonych ze swoimi modelami łącząc elementy modelu z elementami roboczymi programu Team Foundation Server i plan rozwoju. Zobacz [scenariusza: Zmiana projektu z wykorzystaniem wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdej funkcji, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="to"></a>Zadanie  
  
|||  
|-|-|  
|**Wizualizacja kodu**:<br /><br /> — Zobacz organizacją i relacje w kodzie przez utworzenie map kodów. Wizualizacja zależności między zestawów, przestrzeni nazw, klas, metod i tak dalej.<br />— Zobacz klasy, struktury i elementy członkowskie dla określonego projektu, tworząc diagramów klas z kodu.<br />-Znajdowanie konfliktów między kodu i jego projekt, tworząc diagramy warstwowe, aby sprawdzić poprawność kodu.<br /><br /> **Uwaga**: W tej wersji programu Visual Studio termin *mapy kodu* jest używana zamiast *wykres zależności*. Termin *wykres* stosowania samodzielnie zazwyczaj odnosi się do diagramu kierowane wykres lub DGML (lub dokumentu). Mapy kodu są typem wyspecjalizowanym DGML diagram.|-   [Wizualizacja kodu](../modeling/visualize-code.md)<br />-   [Praca z klasami i innymi typami (Projektant klas)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Wideo: Poznanie zależności w kodzie za pomocą wizualizacji (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Wideo: Wizualizacja wpływu zmian (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252068)|  
|**Opisz i informować o wymaganiach użytkowników**:<br /><br /> -Wyjaśnienia historie użytkownika, reguł biznesowych i innych wymagań i zapewnić ich zgodność za pomocą rysowania diagramów UML, takie jak przypadek użycia, działania i diagramy klas.|-   [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)<br />-   [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)<br />-   [Wideo: Poprawa architektury poprzez modelowanie (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)|  
|**Zdefiniuj architektury**:<br /><br /> -Model na dużą skalę strukturę systemu oprogramowania i wzorce projektowe za pomocą rysowania diagram składników UML, klas i diagramów sekwencji.<br />-Definiowanie i wymuszanie ograniczeń zależności między składnikami kodu przez tworzenie diagramów warstwy.|-   [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)<br />-   [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)<br />-   [Wideo: Poprawa architektury poprzez modelowanie (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Wideo: Użyj diagramów warstwowych do projektowania i walidacji architektury (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Weryfikacja systemu z wymaganiami i przeznaczony projektu:**<br /><br /> -Zdefiniować testy odbiorcze lub testy systemu, w oparciu o modele wymagania. Umożliwia utworzenie silnych relacji między testy i wymagania dotyczące użytkowników i pomaga łatwo aktualizować więcej systemu w przypadku zmiany wymagań.<br />— Sprawdzanie poprawności zależności kodu przy użyciu diagramów warstw, które opisują planowaną architekturę i uniemożliwiają zmiany, które mogą powodować konflikty z projektem.|-   [Weryfikacja systemu w czasie projektowania](../modeling/validate-your-system-during-development.md)<br />-   [Wideo: Użyj diagramów warstwowych do projektowania i walidacji architektury (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Udostępnianie modeli, diagramy i map kodu za pomocą kontroli wersji serwera Team Foundation**:<br /><br /> — Umieść mapy kodu, dzięki czemu możesz udostępnić je do modelowania projektów, diagramy UML i diagramów warstwowych w systemie kontroli wersji Team Foundation.|W przypadku wielu użytkowników, którzy pracują z tych elementów w systemie kontroli wersji Team Foundation Użyj następujących wytycznych, co pozwala uniknąć problemów z kontrolą wersji:<br /><br /> -   [Zarządzanie modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Generowanie lub skonfigurować poszczególnych części aplikacji z UML i języków specyficznych dla domeny**:<br /><br /> — Upewnić projektu szybciej reagować na zmiany wymagań i łatwo zmiennych linii produktów.|-   [Generowanie i konfigurowanie aplikacji na podstawie modeli](../modeling/generate-and-configure-your-app-from-models.md)|  
|**Dostosowywanie diagramów i modeli**:<br /><br /> — Dostosuj modele, aby jak projekt korzysta z nich, definiując dodatkowe właściwości elementów UML, ograniczenia sprawdzania poprawności, aby upewnić się, że modele są zgodne z reguł biznesowych i dodatkowym menu poleceń i elementów przybornika.<br />— Utwórz swoje własne języki specyficzne dla domeny.|-   [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK for Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Generowanie tekstu przy użyciu szablonów T4**:<br /><br /> — Użyj bloków tekstu i logiki formantu wewnątrz szablonów do generowania plików tekstowych.|-   [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)|  
  
## <a name="types-of-models-and-their-uses"></a>Typy modeli i ich zastosowań  
  
|**Typ modelu i typowe zastosowania**|  
|-------------------------------------|  
|**Mapy kodu**<br /><br /> Mapy kodu pomagają zobaczyć organizacją i relacje w kodzie.<br /><br /> Typowe zastosowania:<br /><br /> — Sprawdź kod programu, można lepiej zrozumieć jego strukturę i jego zależności, jak zaktualizować go i oszacować koszt proponowane zmiany.<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Diagram warstwowy**<br /><br /> Diagramy warstwowe umożliwiają zdefiniowanie struktury aplikacji jako zestaw warstw lub bloki jawne zależności. Można uruchomić sprawdzania poprawności, aby odnaleźć konfliktów między zależnościami w kodzie i zależności opisane na diagramie warstwy.<br /><br /> Typowe zastosowania:<br /><br /> -Stabilizowanie struktury aplikacji za pomocą liczne zmiany za pośrednictwem jego użytkowania.<br />-Odnajdź konflikty niezamierzonych zależności przed zaewidencjonowaniem zmian w kodzie.<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|  
|**UML model**<br /><br /> UML model zawiera kilka widoków, w tym klasy, składników, przypadków użycia, działania i diagramy sekwencji. Można dostosować UML do własnych domeny aplikacji. Na przykład można dołączyć tagów, dodatkowe informacje i ograniczenia, z elementami modelu. Można również definiować narzędzia, które pracują w modelach. Zobacz [tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md).<br /><br /> Typowe zastosowania:<br /><br /> — Opis wymagań i projektowania. Do tworzenia aplikacji, można szybko zastosować UML. Zobacz [używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md).<br />— Generuje lub skonfigurować testy lub części aplikacji. Część prac jest wymagany do dostosowywania notacji i tworzenie szablonów generowania lub aplikacji można skonfigurować. Zobacz [Generowanie i konfigurowanie aplikacji na podstawie modeli](../modeling/generate-and-configure-your-app-from-models.md).<br />-Ogólny opis i generowanie kodu lub konfiguracji w projektach mniejsze.|  
|**Języka specyficznego dla domeny (DSL)**<br /><br /> DSL jest notacji, która projektowania do określonego celu. W programie Visual Studio jest zazwyczaj graficznego.<br /><br /> Typowe zastosowania:<br /><br /> — Generuje lub skonfigurować części aplikacji. Praca jest wymagany do tworzenia, narzędzia i notacji. Wynik może być lepszym rozwiązaniem niż dostosowywania UML do domeny.<br />— W przypadku dużych projektów lub linii produktów, w którym inwestycji w opracowywaniu język DSL i jego narzędzi jest zwracany przez jej użycie w więcej niż jeden projekt.<br /><br /> Zobacz:<br /><br /> -   [Modeling SDK for Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?  
  
|||  
|-|-|  
|**Fora**|-   [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Zobacz też  
 [Co nowego](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps i zarządzanie cyklem życia aplikacji](http://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
