---
title: Właściwości kształtów geometrycznych
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1088dafea1c43e624d029de6b890c9b597b061
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658177"
---
# <a name="properties-of-geometry-shapes"></a>Właściwości kształtów geometrycznych
Można użyć kształtów geometrycznych, aby określić, jak wystąpienia klas domeny są wyświetlane w języku specyficznym dla domeny. Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Kształty geometryczne mają właściwości, które są wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślny|
|-|-|-|
|Kolor wypełnienia|Kolor wypełnienia tego kształtu.|oficjaln|
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu (poziomy, pionowy, przekątna ukośna, przekątna do tyłu lub brak).|Układ|
|Geometrii|Geometria tego kształtu (prostokąt, prostokąt zaokrąglony, Elipsa lub koło).|prostokąt|
|Ma domyślne punkty połączenia|Jeśli `True`, kształt będzie korzystać z górnego, dolnego, lewego i prawego punktu połączenia w wygenerowanym projektancie.|False|
|Kolor konturu|Kolor konturu tego kształtu.|gasić|
|Styl kreskowania konturu|Styl kreskowania konturu tego kształtu (pełny, kreska, kropka, DashDot, DashDotDot lub niestandardowy).|Wypełnione|
|Grubość konturu|Grubość konturu tego kształtu.|0,03125|
|Kolor tekstu|Kolor używany dla dekoratory tekstu, które są skojarzone z tym kształtem.|gasić|
|Modyfikator dostępu|Modyfikator dostępu klasy (Public lub internal).|Public|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana dla tego kształtu.|\<none >|
|Generuje podwójny pochodny|Jeśli `True`, zostaną wygenerowane zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Ma Konstruktor niestandardowy|Jeśli `True`, Konstruktor niestandardowy zostanie udostępniony w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana na podstawie kształtu (`none`, `abstract` lub `sealed`).|brak|
|Podstawowy kształt geometrii|Klasa bazowa tego kształtu.|dawaj|
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest powiązana z tym kształtem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Sposób definiowania etykietki narzędzia (stała, zmienna lub brak). Jeśli stała, wartość właściwości `Fixed Tooltip Text` jest używana jako etykietka narzędzia; Jeśli zmienna, wówczas etykietka narzędzia jest definiowana w kodzie niestandardowym.|Brak|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym elementem.|\<none >|
|Początkowa wysokość|Początkowa wysokość tego kształtu (w calach).|1|
|Szerokość początkowa|Początkowa Szerokość tego kształtu, w calach.|1,5|
|Uwidoczniony kolor wypełnienia jako właściwość<br /><br /> Uwidaczniany tryb gradientu wypełnienia<br /><br /> Uwidoczniony kolor konturu jako właściwość<br /><br /> Uwidoczniony styl kreskowania konturu jako właściwość<br /><br /> Uwidoczniona grubość konturu jako właściwość<br /><br /> Uwidacznia kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość wartość dla kształtu. Aby ustawić tę opcję, kliknij prawym przyciskiem myszy definicję kształtu, a następnie kliknij pozycję **Dodaj uwidocznione**.|False|
|Opis|Opis używany do dokumentowania wygenerowanego projektanta.|\<none >|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego kształtu.|\<none >|
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałej etykietki narzędzia.|\<none >|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego kształtu.|\<none >|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)