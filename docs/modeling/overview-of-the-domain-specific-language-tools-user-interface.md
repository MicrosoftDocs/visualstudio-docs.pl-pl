---
title: Omówienie interfejsu użytkownika narzędzi językowych właściwych dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d54ba969e06f3bd951556f8d8f347977419fc015
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966495"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Omówienie interfejsu użytkownika narzędzi językowych właściwych dla domeny
Przy pierwszym otwarciu rozwiązania narzędzia języka specyficznego dla domeny (narzędzia DSL) w programie Visual Studio, interfejs użytkownika będzie przypominał poniższej ilustracji.

 ![Projektant DSL](../modeling/media/dsl_designer.png)

 W poniższej tabeli opisano, jak są używane elementy interfejsu użytkownika.

|**Element**|**Definicja**|
|-|-|
|Diagram|Model domeny są wyświetlane na diagramie.<br /><br /> Diagram ma dwie strony. Z jednej strony definiuje typy elementów w ramach modeli. Druga strona definiuje wygląd swoje modele na ekranie.|
|Przybornik|Przeciągnij narzędzia z przybornika, aby dodać klasy domeny i kształtów typów do diagramu. Aby dodać relacje, łączników i mapowania kształtów, kliknij narzędzie, a następnie kliknij węzeł źródła na diagramie, a następnie węzeł docelowy.|
|Eksplorator modelu DSL|**Eksplorator modelu DSL** jest wyświetlany, gdy w definicji DSL jest aktywnym oknem. Język DSL jest wyświetlany jako drzewa. Eksplorator modelu DSL pozwala edytować funkcje modelu, które nie są wyświetlane na diagramie. Na przykład Dodaj elementy przybornika i przełączać w trakcie procesu walidacji za pomocą **Eksplorator DSL**.|
|Okno Szczegóły języka DSL|**Szczegóły języka DSL** okno pokazuje właściwości domeny elementy modelu, które pozwalają kontrolować sposób wyświetlania elementów i jak elementy są kopiowane i usunąć.<br /><br /> -Domyślnie **szczegóły języka DSL** okno jest wyświetlane obok pola **lista błędów** i **dane wyjściowe** systemu windows.|

## <a name="the-domain-model-diagram"></a>Diagram modelu domeny
 Diagram modelu domeny jest podzielona na dwie części. Po jednej stronie diagramu zawiera określone elementy i relacje w modelu. Druga strona pokazuje, jak model, który jest wyświetlany i zawiera kształty, które są używane do wyświetlania elementów i właściwości diagramu modelu. Na poniższej ilustracji przedstawiono elementy diagramu.

 ![Projektant DSL za pomocą toru](../modeling/media/dsl_desinger.png)

 W poniższej tabeli opisano niektóre elementy diagramu modelu domeny.

|**Termin**|**Definicja**|
|-|-|
|Klasa domeny|Klasy domeny są typy elementów w ramach modeli.<br /><br /> Klasy domeny może występować więcej niż jeden raz na diagramie, jeśli jest to element docelowy więcej niż jedną relację.<br /><br /> Aby dodać klasę domeny, przeciągnij narzędzie klasę domeny z **przybornika** do **klasy i relacje** stronie diagramu.|
|Relacja domeny|Relacje domeny są typy łączy między elementami w ramach modeli.<br /><br /> *Relacja osadzania* wskazuje, czy element docelowy jest właścicielem lub zawartej w elemencie źródłowym i jest wyświetlany jako linię ciągłą. Każdy element w modelu należy celem jedna relacja osadzania, tak, czy model formularzy drzewa. A *odwoływać się do relacji* oznacza ogólne łącza między elementami modelu i jest wyświetlana jako linia przerywana. Każdy element może mieć dowolną liczbę łączy odnośnika.<br /><br /> Utwórz relację, klikając narzędzie **przybornika**, klikając klasy domeny źródłowej, a następnie klikając klasy docelowej.|
|Kształty i łączniki|Kształty, określ, jak elementy modelu powinien być wyświetlany na diagram DSL., łączników określić wiersze na diagramie DSL, który może służyć do wyświetlania relacji.<br /><br /> Aby utworzyć łącznik lub kształt, przeciągnij narzędzie do **elementów diagramu** stronie diagramu.|
|Mapowania kształtów|Mapowanie kształtów pojawia się jako linia na diagram modelu domeny, konsolidacji kształt do klasy domeny, który jest wyświetlany, lub łącznik do relacji domeny, który jest wyświetlany.|

## <a name="see-also"></a>Zobacz też

- [Przegląd narzędzi języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)