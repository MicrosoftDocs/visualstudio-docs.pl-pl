---
title: Omówienie interfejsu użytkownika Domain-Specific Language Tools
description: Zawiera omówienie interfejsu użytkownika rozwiązania narzędzi języka specyficznego dla domeny w Visual Studio.
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 4fe826b373ba2ee468bfe511392eb5564234dc68
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390961"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Omówienie interfejsu użytkownika narzędzi językowych właściwych dla domeny
Po pierwszym otwarciu rozwiązania Domain-Specific Language Tools (DSL Tools) w języku Visual Studio interfejs użytkownika będzie wyglądać jak na poniższej ilustracji.

 ![dsl designer](../modeling/media/dsl_designer.png)

 W poniższej tabeli wyjaśniono, jak są używane części interfejsu użytkownika.

|**Element**|**Definicja**|
|-|-|
|Diagram|Diagram przedstawia model domeny.<br /><br /> Diagram ma dwie strony. Jedna strona definiuje typy elementów w modelach. Druga strona definiuje sposób, w jaki modele będą wyświetlane na ekranie.|
|Przybornik|Przeciągnij narzędzia z przybornika, aby dodać klasy domen i typy kształtów do diagramu. Aby dodać relacje, łączniki i mapy kształtów, kliknij narzędzie, a następnie kliknij węzeł źródłowy na diagramie, a następnie węzeł docelowy.|
|Eksplorator modelu DSL|**Eksplorator DSL jest** wyświetlany, gdy aktywne jest okno definicji DSL. Pokazuje DSL jako drzewo. Eksplorator DSL umożliwia edytowanie funkcji modelu, które nie są wyświetlane na diagramie. Można na przykład dodać elementy przybornika i przełączyć proces weryfikacji przy użyciu **eksploratora DSL**.|
|Okno szczegółów DSL|Okno **Szczegóły DSL** zawiera właściwości elementów modelu domeny, które umożliwiają kontrolowanie sposobu wyświetlania elementów oraz sposobu kopiowania i usunięcia elementów.<br /><br /> - Domyślnie okno **Szczegóły DSL** jest wyświetlane obok okien **Lista** błędów i **Dane** wyjściowe.|

## <a name="the-domain-model-diagram"></a>Diagram modelu domeny
 Diagram modelu domeny jest podzielony na dwie części. Po jednej stronie diagramu przedstawiono elementy i relacje w modelu. Druga strona pokazuje sposób wyświetlania modelu i zawiera kształty, które są używane do wyświetlania elementów i właściwości diagramu modelu. Na poniższej ilustracji przedstawiono elementy diagramu.

 ![dsl designer with tolane (projektant dsl z toriem)](../modeling/media/dsl_desinger.png)

 W poniższej tabeli wyjaśniono niektóre elementy diagramu modelu domeny.

|**Okres**|**Definicja**|
|-|-|
|Klasa domeny|Klasy domen to typy elementów w modelach.<br /><br /> Klasa domeny może pojawić się na diagramie więcej niż raz, jeśli jest obiektem docelowym więcej niż jednej relacji.<br /><br /> Aby dodać klasę domeny, przeciągnij narzędzie  klasy domeny z przybornika do strony **Klasy i** relacje diagramu.|
|Relacja domeny|Relacje domeny to typy linków między elementami w modelach.<br /><br /> Relacja *osadzania wskazuje,* że element docelowy jest własnością elementu źródłowego lub jest przez nie zawarty, i pojawia się jako linia ciągła. Każdy element w modelu powinien być obiektem docelowym jednej relacji osadzania, tak aby model tworzył drzewo. Relacja *referencyjna* wskazuje ogólne połączenie między elementami modelu i jest wyświetlana jako linia przerywana. Każdy element może mieć dowolną liczbę linków odwołania.<br /><br /> Utwórz relację, klikając narzędzie w przyborniku **,** klikając klasę domeny źródłowej, a następnie klikając klasę docelową.|
|Kształty i łączniki|Kształty określają sposób wyświetlania elementów modelu na diagramie DSL. Łączniki określają linie na diagramie DSL, które mogą służyć do wyświetlania relacji.<br /><br /> Aby utworzyć kształt lub łącznik, przeciągnij narzędzie do strony **Elementy diagramu** diagramu.|
|Mapy kształtów|Mapa kształtów jest wyświetlana jako linia na diagramie modelu domeny, łącząc kształt z klasą domeny, która jest wyświetlana, lub łącznikiem z wyświetlaną relacją domeny.|

## <a name="see-also"></a>Zobacz też

- [Przegląd narzędzi języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))
- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)