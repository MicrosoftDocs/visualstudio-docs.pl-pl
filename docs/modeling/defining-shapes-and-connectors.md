---
title: Definiowanie kształtów i łączników
description: Dowiedz się więcej o kilku podstawowych typach kształtów, których można użyć do wyświetlania informacji na diagramie w języku specyficznym dla domeny (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 622ff598ac2471814e51b0e268c12d40e726fb98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385750"
---
# <a name="define-shapes-and-connectors"></a>Definiowanie kształtów i łączników

Istnieje kilka podstawowych typów kształtów, których można użyć do wyświetlania informacji na diagramie w języku specyficznym dla domeny (DSL).

## <a name="basic-types-of-shapes-and-connectors"></a><a name="shapeTypes"></a> Podstawowe typy kształtów i łączników

Diagram DSL przedstawia kolekcję *kształtów* połączonych liniami lub *łącznikami*. Zwykle, ale nie zawsze:

- Kształty są widoczną reprezentacją elementów modelu.

- Łączniki reprezentują relacje odwołania.

- Diagram reprezentuje wystąpienie główne modelu.

- Osadzanie relacji między elementami modelu jest wyświetlane przez zawieranie. Na przykład elementy reprezentujące porty składników są osadzone w składniku.

Te wzorce nie są wymuszane, ale są bardziej obsługiwane. Podczas projektowania DSL należy pamiętać, że na projekt relacji osadzania powinien mieć wpływ sposób prezentowania modelu na ekranie. Z kolei relacje odwoływujące powinny odzwierciedlać koncepcje twojej domeny biznesowej.

Dostępne są następujące typy kształtów:

|Typ kształtu|Opis|
|-|-|
|Kształt geometrii|Prostokątny lub eliptyczny kształt ogólnego przeznaczenia. Można wyświetlać dekoratory tekstu i ikon w określonych pozycjach względem granic kształtu. Możesz również zagnieżdżać kształty wewnątrz kształtów geometrycznych.|
|Kształt przedziału|Prostokąt zawierający nagłówek i przedziały, takie jak klasa UML. Każdy przedział może zawierać listę wierszy tekstowych.<br /><br /> Wiersze zazwyczaj reprezentują elementy osadzone pod elementem reprezentowanym przez kształt. Na przykład utwórz DSL na podstawie szablonu rozwiązania Diagramy klas.|
|Kształt obrazu|Kształt, który wyświetla obraz.|
|Kształt portu|Mały prostokąt przeznaczony do dołączania do konturu innego kształtu. Zwykle używany w modelach składników.<br /><br /> Element modelu reprezentowany przez port jest zwykle osadzony w elemencie reprezentowanym przez kształt nadrzędny. Na przykład utwórz DSL przy użyciu szablonu rozwiązania Składniki.<br /><br /> Domyślnie kształt portu może przesuwać się wzdłuż jego krawędzi nadrzędnej. Można zdefiniować regułę granic, aby ograniczyć ją do określonej pozycji.<br /><br /> Dzięki temu, że kształt portu jest bardzo mały i przezroczysty, można go użyć do zapewnienia stałego punktu połączenia na powierzchni jego kształtu nadrzędnego.|
|Torów|Tory partycjonują diagram na segmenty poziome lub pionowe. Tor zawsze pozostaje poniżej innych kształtów na diagramie.<br /><br /> Zazwyczaj elementy modelu toru są nadrzędne w katalogu głównym modelu, a inne elementy są na nich nadrzędne. Na przykład utwórz DSL na podstawie szablonu rozwiązania przepływu zadań.|
|Łączniki|Linie narysowane między kształtami zazwyczaj reprezentują relacje odwołania. Możesz ustawić opcje, aby łącznik był prosty lub wyrównany oraz miał różne typy strzałek.|

## <a name="shape-inheritance"></a>Dziedziczenie kształtów

Kształt może dziedziczyć z innego kształtu. Jednak kształty muszą być tego samego rodzaju. Na przykład tylko kształt geometrii może dziedziczyć z kształtu geometrii. Dziedziczone kształty mają przedziały i dekoratory o kształcie bazowym. Łączniki mogą dziedziczyć z łączników.
