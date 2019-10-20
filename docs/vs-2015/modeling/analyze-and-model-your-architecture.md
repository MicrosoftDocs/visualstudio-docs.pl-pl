---
title: Analizowanie i modelowanie architektury | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38a65a98c1dca5542d3e0e667cb623283bb164c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602420"
---
# <a name="analyze-and-model-your-architecture"></a>Analizowanie i modelowanie architektury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upewnij się, że Twoja aplikacja spełnia wymagania użytkowników, używając architektury programu Visual Studio i narzędzi modelowania do projektowania i modelowania aplikacji. Łatwiejsze zrozumienie istniejącego kodu programu przy użyciu programu Visual Studio do wizualizacji struktury kodu, zachowania i relacji.

 Twórz modele na różnych poziomach szczegółowości w całym cyklu życia aplikacji w ramach procesu tworzenia oprogramowania. Śledź wymagania, zadania, przypadki testowe, błędy i inne prace skojarzone z modelami, łącząc elementy modelu z Team Foundation Server elementami roboczymi i planem rozwoju. Zobacz [Scenariusz: Zmień projekt przy użyciu wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Aby sprawdzić, które wersje programu Visual Studio obsługują każdą funkcję, zobacz [Obsługa wersji dla narzędzi architektura i modelowanie](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="to"></a>Do

|||
|-|-|
|**Wizualizuj kod**:<br /><br /> — Zobacz temat organizacja i relacje kodu, tworząc mapy kodu. Wizualizuj zależności między zestawami, przestrzeniami nazw, klasami, metodami i tak dalej.<br />-Zobacz strukturę klas i składowe dla określonego projektu, tworząc diagramy klas z kodu.<br />— Znajdź konflikty między kodem i projektem, tworząc diagramy warstwowe do walidacji kodu.<br /><br /> **Uwaga**: w tej wersji programu Visual Studio termin *Mapa kodu* jest używana zamiast *grafu zależności*. Termin " *Wykres* " używany samodzielnie zwykle odwołuje się do wykresu lub diagramu DGML (lub dokumentu). Mapy kodu są wyspecjalizowanym typem diagramu DGML.|-   [wizualizacji kodu](../modeling/visualize-code.md)<br />-   [pracy z klasami i innymi typami (Projektant klas)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [wideo: zrozumienie zależności kodu za pośrednictwem wizualizacji (kanał 9)](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [wideo: wizualizowanie wpływu zmiany (kanał 9)](http://go.microsoft.com/fwlink/?LinkID=252068)|
|**Opisz i przekaż wymagania dotyczące użytkowników**:<br /><br /> -Wyjaśnij historie użytkowników, reguły biznesowe i inne wymagania, aby zapewnić ich spójność poprzez Rysowanie diagramów UML, takich jak diagramy przypadków użycia, działania i klas.|-   [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md)<br />[wymagania dotyczące użytkownika modelu](../modeling/model-user-requirements.md) -   <br />-   [wideo: ulepszanie architektury za pośrednictwem modelowania (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)|
|**Zdefiniuj architekturę**:<br /><br /> -Modelowanie struktury dużej skali systemu oprogramowania i wzorców projektowych przez rysowanie składników UML, klas i diagramów sekwencji.<br />-Zdefiniuj i wymuś ograniczenia zależności między składnikami kodu przez utworzenie diagramów warstwowych.|-   [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md)<br />-   [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)<br />-   [wideo: ulepszanie architektury za pośrednictwem modelowania (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [wideo: używanie diagramów warstw do projektowania i weryfikowania architektury (kanał 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|
|**Sprawdź, czy system spełnia wymagania i zamierzony projekt:**<br /><br /> -Zdefiniuj testy akceptacji lub testy systemowe na podstawie modeli wymagań. Dzięki temu można utworzyć silną relację między testami i wymaganiami użytkowników, a tym samym łatwiej aktualizować system w przypadku zmiany wymagań.<br />-Weryfikuj zależności kodu przy użyciu diagramów warstw, które opisują zamierzoną architekturę i zapobiegają zmianom, które mogą powodować konflikty z projektem.|-   [Weryfikuj system podczas opracowywania](../modeling/validate-your-system-during-development.md)<br />-   [wideo: używanie diagramów warstw do projektowania i weryfikowania architektury (kanał 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|
|**Udostępnianie modeli, diagramów i map kodu przy użyciu kontroli wersji programu Team Foundation**:<br /><br /> -Umieszczaj mapy kodu, projekty modelowania, diagramy UML i diagramy warstwowe w ramach kontroli wersji programu Team Foundation, aby można było je udostępnić.|Jeśli masz wielu użytkowników, którzy pracują z tymi elementami w ramach kontroli wersji programu Team Foundation, Skorzystaj z poniższych wskazówek, aby uniknąć problemów z kontrolą wersji:<br /><br /> -   [zarządzać modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Generuj lub Konfiguruj części aplikacji z poziomu UML lub języków specyficznych dla domeny**:<br /><br /> — Zwiększ możliwości projektu, aby zwiększyć wymagania i łatwo zmienne w linii produktów.|-   [generowanie i Konfigurowanie aplikacji na podstawie modeli](../modeling/generate-and-configure-your-app-from-models.md)|
|**Dostosuj modele i diagramy**:<br /><br /> -Dostosowanie modeli do sposobu, w jaki projekt używa ich przez definiowanie dodatkowych właściwości elementów UML, ograniczeń sprawdzania poprawności, aby upewnić się, że modele są zgodne z regułami biznesowymi i dodatkowymi poleceniami menu i elementami przybornika.<br />— Tworzenie własnych języków specyficznych dla domeny.|-   [poszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK dla programu Visual Studio — Języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generuj tekst przy użyciu szablonów T4**:<br /><br /> -Używaj bloków tekstowych i logiki formantów wewnątrz szablonów do generowania plików tekstowych.|-   [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Typy modeli i ich zastosowania

|**Typ modelu i typowe zastosowania**|
|-------------------------------------|
|**Mapy kodu**<br /><br /> Mapy kodu pomagają zobaczyć organizację i relacje w kodzie.<br /><br /> Typowe zastosowania:<br /><br /> -Badaj kod programu, aby lepiej zrozumieć swoją strukturę i jej zależności, jak ją zaktualizować, i oszacować koszt proponowanych zmian.<br /><br /> Zobacz:<br /><br /> -   [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [użyć map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Znajdowanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Diagram warstwowy**<br /><br /> Diagramy warstw pozwalają definiować strukturę aplikacji jako zestaw warstw lub bloków z jawnymi zależnościami. Można uruchomić walidację w celu odnalezienia konfliktów między zależnościami w kodzie i zależnościami opisanymi na diagramie warstwowym.<br /><br /> Typowe zastosowania:<br /><br /> — Stabilizacja struktury aplikacji dzięki licznym zmianom w jego życiu.<br />-Odkryj nieumyślne konflikty zależności przed zaewidencjonowaniem zmian w kodzie.<br /><br /> Zobacz:<br /><br /> -   [tworzenia diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy warstwowe: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Weryfikuj kod przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|
|**Model UML**<br /><br /> Model UML zawiera kilka widoków, takich jak Klasa, składnik, przypadek użycia, działanie i diagramy sekwencji. Można dostosować UML do domeny aplikacji. Na przykład możesz dołączyć Tagi, dodatkowe informacje i ograniczenia do elementów modelu. Można także definiować narzędzia, które działają w modelach. Zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md).<br /><br /> Typowe zastosowania:<br /><br /> -Opisz wymagania i projekt. Możesz szybko zastosować UML do rozwoju dowolnej aplikacji. Zobacz [Używanie modeli w procesie tworzenia oprogramowania](../modeling/use-models-in-your-development-process.md).<br />— Generowanie lub Konfigurowanie testów lub części aplikacji. Niektóre prace są wymagane do dostosowania notacji i opracowania szablonów generacji lub aplikacji konfigurowalnej. Zobacz [generowanie i Konfigurowanie aplikacji na podstawie modeli](../modeling/generate-and-configure-your-app-from-models.md).<br />— W przypadku ogólnego opisu i generowania kodu lub konfiguracji w mniejszych projektach.|
|**Język specyficzny dla domeny (DSL)**<br /><br /> DSL to notacja, którą można zaprojektować w określonym celu. W programie Visual Studio jest zwykle graficzny.<br /><br /> Typowe zastosowania:<br /><br /> — Generowanie lub Konfigurowanie części aplikacji. Do opracowania notacji i narzędzi wymagane jest działanie. Wynik może być lepszym dopasowaniem do domeny niż dostosowanie UML.<br />— W przypadku dużych projektów lub w wierszach produktu, w których inwestycje w programowanie DSL i jej narzędzia są zwracane przez użycie w więcej niż jednym projekcie.<br /><br /> Zobacz:<br /><br /> -   [Modeling SDK dla programu Visual Studio — Języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?

|||
|-|-|
|**Dotyczące**|-   [Wizualizacja programu Visual Studio & narzędzia do modelowania](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [wizualizacji programu Visual Studio & Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Zobacz też

- [Nowości dotyczące modelowania w programie Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps i zarządzanie cyklem życia aplikacji](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
