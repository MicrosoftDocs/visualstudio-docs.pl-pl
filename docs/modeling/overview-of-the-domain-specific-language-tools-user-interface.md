---
title: Omówienie interfejsu użytkownika narzędzi językowych właściwych dla domeny
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af28ca94639b1c6a800c0c43e41d3ccabb74d9bb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532408"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Omówienie interfejsu użytkownika narzędzi językowych właściwych dla domeny
Po pierwszym otwarciu rozwiązania narzędzia języka specyficznego dla domeny (narzędzia DSL) w programie Visual Studio interfejs użytkownika będzie wyglądał na poniższym obrazie.

 ![Projektant DSL](../modeling/media/dsl_designer.png)

 W poniższej tabeli opisano, jak są używane części interfejsu użytkownika.

|**Postaci**|**Definicja**|
|-|-|
|Diagram|Na diagramie zostanie wyświetlony model domeny.<br /><br /> Diagram ma dwie strony. Jedna strona definiuje typy elementów w modelach. Druga strona definiuje sposób wyświetlania modeli na ekranie.|
|Przybornik|Przeciągnij narzędzia z przybornika, aby dodać klasy domeny i typy kształtów do diagramu. Aby dodać relacje, łączniki i mapy kształtów, kliknij narzędzie, a następnie kliknij węzeł źródłowy na diagramie, a następnie węzeł docelowy.|
|Eksplorator modelu DSL|**Eksplorator DSL** jest wyświetlany, gdy Definicja DSL jest oknem aktywnym. Pokazuje DSL jako drzewo. Eksplorator DSL umożliwia edytowanie funkcji modelu, które nie są wyświetlane na diagramie. Na przykład możesz dodać elementy przybornika i przełączać się do procesu walidacji za pomocą **Eksploratora DSL**.|
|Okno szczegółów DSL|W oknie **Szczegóły DSL** są wyświetlane właściwości elementów modelu domeny, które umożliwiają kontrolowanie sposobu wyświetlania elementów oraz sposobu kopiowania i usuwania elementów.<br /><br /> -Domyślnie okno **Szczegóły DSL** pojawia się obok okna **Lista błędów** i **danych wyjściowych** .|

## <a name="the-domain-model-diagram"></a>Diagram modelu domeny
 Diagram modelu domeny jest podzielony na dwie części. Jedna ze stron diagramu pokazuje elementy i relacje w modelu. Druga strona pokazuje, jak model ma być wyświetlany, i zawiera kształty, które są używane do wyświetlania elementów i właściwości diagramu modelu. Na poniższej ilustracji przedstawiono elementy diagramu.

 ![Projektant DSL z torem](../modeling/media/dsl_desinger.png)

 W poniższej tabeli objaśniono niektóre elementy diagramu modelu domeny.

|**Termin**|**Definicja**|
|-|-|
|Klasa domeny|Klasy domeny są typami elementów w modelach.<br /><br /> Klasa domeny może pojawić się więcej niż jeden raz w diagramie, jeśli jest elementem docelowym więcej niż jednej relacji.<br /><br /> Aby dodać klasę domeny, przeciągnij narzędzie klasy domeny z **przybornika** do strony **klasy i relacje** na diagramie.|
|Relacja domeny|Relacje domen są typami linków między elementami modeli.<br /><br /> *Relacja osadzania* wskazuje, że element docelowy jest własnością lub znajduje się w elemencie źródłowym i pojawia się jako linia ciągła. Każdy element w modelu powinien być elementem docelowym jednej relacji osadzania, dzięki czemu model tworzy drzewo. *Relacja odwołania* wskazuje ogólny link między elementami modelu i pojawia się jako linia kreskowana. Każdy element może mieć dowolną liczbę linków odwołania.<br /><br /> Utwórz relację, klikając narzędzie w **przyborniku**, klikając klasę domena źródłowa, a następnie klikając klasę docelową.|
|Kształty i łączniki|Kształty określają sposób wyświetlania elementów modelu na diagramie DSL. łączniki określają linie na diagramie DSL, których można użyć do wyświetlania relacji.<br /><br /> Aby utworzyć kształt lub łącznik, przeciągnij narzędzie do strony **elementy diagramu** na diagramie.|
|Mapy kształtów|Mapa kształtów jest wyświetlana jako linia na diagramie modelu domeny, łącząca kształt z klasą domeny, która jest wyświetlana, lub łącznikiem z wyświetlaną relacją domeny.|

## <a name="see-also"></a>Zobacz także

- [Przegląd narzędzi języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
- [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)
