---
title: Definiowanie kształtów i łączników | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8304e573f64671936eee2ce922b904b41187aad2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669855"
---
# <a name="defining-shapes-and-connectors"></a>Definiowanie kształtów i łączników
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Istnieje kilka podstawowych typów kształtów, których można użyć do wyświetlania informacji na diagramie w języku specyficznym dla domeny (DSL).

## <a name="shapeTypes"></a>Podstawowe typy kształtów i łączników
 Diagram DSL przedstawia kolekcję *kształtów* połączonych przez linie lub *Łączniki*.  Zwykle, ale nie zawsze:

- Kształty są widoczną reprezentacją elementów modelu.

- Łączniki reprezentują relacje odwołania.

- Diagram reprezentuje wystąpienie elementu głównego modelu.

- Relacje osadzania między elementami modelu są wyświetlane przez zawieranie. Na przykład elementy reprezentujące porty składników są osadzone w składniku.

  Te wzorce nie są wymuszane, ale są bardziej silnie obsługiwane. Podczas projektowania DSL należy pamiętać, że projekt relacji osadzania powinien wpływać na to, w jaki sposób chcesz przedstawić model na ekranie. Z kolei relacje odwołania powinny odzwierciedlać koncepcje Twojej domeny biznesowej.

  Dostępne są następujące typy kształtów:

|Typ kształtu|Opis|
|----------------|-----------------|
|Kształt geometrii|Kształt prostokątny ogólnego przeznaczenia lub elipsy. Możesz wyświetlić tekst i ikonę dekoratory w określonych miejscach względem granic kształtu.<br /><br /> Aby zagnieżdżać kształty wewnątrz kształtów geometrycznych, zobacz [Zagnieżdżanie kształtów](../modeling/nesting-shapes.md).|
|Kształt przedziału|Prostokąt zawierający nagłówek i przedziały, takie jak Klasa UML. Każdy przedział może zawierać listę wierszy tekstu.<br /><br /> Wiersze zazwyczaj reprezentują elementy osadzone w elemencie reprezentowane przez kształt. Aby zapoznać się z przykładem, Utwórz DSL z szablonu rozwiązania diagramy klas.|
|Kształt obrazu|Kształt wyświetlający obraz.|
|Kształt portu|Mały prostokąt zaprojektowany do dołączenia do konturu innego kształtu. Zwykle używane w modelach składników.<br /><br /> Element modelu reprezentowany przez port jest zwykle osadzony w elemencie reprezentowanym przez kształt nadrzędny. Aby zapoznać się z przykładem, Utwórz DSL przy użyciu szablonu rozwiązania składniki.<br /><br /> Domyślnie kształt portu może przesuwać się wzdłuż krawędzi jego elementu nadrzędnego. Można zdefiniować regułę ograniczenia, aby ograniczyć ją do określonego położenia.<br /><br /> Dzięki czemu kształt portu jest bardzo mały i niewidoczny, można go użyć do zapewnienia stałego punktu połączenia na powierzchni jego kształtu nadrzędnego.|
|Torów|Tory dzielą diagram na segmenty w poziomie lub w pionie. Tor zawsze pozostaje poniżej innych kształtów na diagramie.<br /><br /> Zazwyczaj elementy modelu toru są nadrzędne w katalogu głównym modelu, a inne elementy są na nich nadrzędne. Aby zapoznać się z przykładem, Utwórz DSL przy użyciu szablonu rozwiązania przepływu zadań.|
|Wtyczki|Linie rysowane między kształtami zwykle reprezentują relacje odwołania. Można ustawić opcje, aby utworzyć Łącznik prostoliniowy lub Rectilinear, a także mieć różne typy grotów strzałek.|

## <a name="shapeInheritance"></a>Dziedziczenie kształtów
 Kształt może dziedziczyć z innego kształtu. Jednak kształty muszą być tego samego rodzaju. Na przykład tylko kształt geometryczny może dziedziczyć z kształtu geometrycznego. Dziedziczone kształty mają przedziały i dekoratory ich kształtu podstawowego. Łączniki mogą dziedziczyć po łącznikach.
