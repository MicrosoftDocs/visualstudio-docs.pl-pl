---
title: Omówienie interfejsu użytkownika narzędzi językowych specyficznych dla domeny | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bffb1f7fe6449f078c21c14b0a070cbd23db539
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72652134"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Omówienie interfejsu użytkownika narzędzi językowych właściwych dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po pierwszym otwarciu rozwiązania narzędzia języka specyficzne dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]domeny (DSL Tools) w , interfejs użytkownika będzie podobny do następującego obrazu.

 ![projektant dsl](../modeling/media/dsl-designer.png "dsl_designer")

 W poniższej tabeli wyjaśniono, jak używane są części interfejsu użytkownika.

|**Element**|**Definicja**|
|-----------------|--------------------|
|Diagram|Na diagramie jest wyświetlany model domeny.<br /><br /> Diagram ma dwie strony. Jedna strona definiuje typy elementów w modelach. Druga strona określa sposób, w jaki modele będą wyświetlane na ekranie.|
|Przybornik|Przeciągnij narzędzia z przybornika, aby dodać klasy domen i typy kształtów do diagramu. Aby dodać relacje, łączniki i mapy kształtów, kliknij narzędzie, a następnie kliknij węzeł źródłowy na diagramie, a następnie węzeł docelowy.|
|Eksplorator modelu DSL|**Eksplorator DSL** pojawia się, gdy definicja DSL jest aktywnym oknem. Pokazuje DSL jako drzewo. Dsl Explorer umożliwia edycję operacji modelu, które nie są wyświetlane na diagramie. Na przykład można dodać elementy przybornika i włączyć proces sprawdzania poprawności za pomocą **Eksploratora DSL**.|
|Okno Szczegóły DSL|Okno **Szczegóły DSL** zawiera właściwości elementów modelu domeny, które umożliwiają kontrolowanie sposobu wyświetlania elementów oraz sposobu kopiowania i usuwania elementów.<br /><br /> - Domyślnie okno **Szczegóły DSL** jest wyświetlane obok **okien Lista błędów** i **Dane wyjściowe.**|

## <a name="the-domain-model-diagram"></a>Diagram modelu domeny
 Diagram modelu domeny jest podzielony na dwie części. Po jednej stronie diagramu przedstawiono elementy i relacje w modelu. Druga strona pokazuje, jak model ma być wyświetlany i zawiera kształty, które są używane do wyświetlania elementów i właściwości diagramu modelu. Na poniższej ilustracji przedstawiono elementy diagramu.

 ![projektant dsl z tokiem](../modeling/media/dsl-desinger.png "dsl_desinger")

 W poniższej tabeli wyjaśniono niektóre elementy diagramu modelu domeny.

|**Termin**|**Definicja**|
|--------------|--------------------|
|Klasa domeny|Klasy domeny są typami elementów w modelach.<br /><br /> Klasa domeny może pojawić się więcej niż jeden raz na diagramie, jeśli jest obiektem docelowym więcej niż jednej relacji.<br /><br /> Aby dodać klasę domeny, przeciągnij narzędzie klasy domeny z **przybornika** do strony **Klasy i Relacje** diagramu.|
|Relacja między domenami|Relacje domeny są typami łączy między elementami w modelach.<br /><br /> Relacja *osadzania* wskazuje, że element docelowy jest własnością lub zawiera element źródłowy i jest wyświetlany jako linia ciągła. Każdy element w modelu powinien być celem jednej relacji osadzania, tak aby model tworzył drzewo. *Relacja odniesienia* wskazuje ogólne łącze między elementami modelu i jest wyświetlana jako linia przerywana. Każdy element może mieć dowolną liczbę łączy referencyjnych.<br /><br /> Utwórz relację, klikając narzędzie w **przyborniku**, klikając klasę domeny źródłowej, a następnie klikając klasę docelową.|
|Kształty i łączniki|Kształty określają sposób wyświetlania elementów modelu na diagramie DSL., Łączniki określają linie na diagramie DSL, które mogą być używane do wyświetlania relacji.<br /><br /> Aby utworzyć kształt lub łącznik, przeciągnij narzędzie na stronę **Diagramu Elementy** diagramu.|
|Mapy kształtów|Mapa kształtu jest wyświetlana jako linia na diagramie modelu domeny, łącząca kształt z wyświetlaną klasą domeny lub łącznikiem do wyświetlanej przez nią relacji domeny.|

## <a name="see-also"></a>Zobacz też
 [Omówienie glosariusza](../modeling/overview-of-domain-specific-language-tools.md) Narzędzia językowe specyficzne dla domeny narzędzia [językowe specyficzne dla](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) domeny [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)
