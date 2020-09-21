---
title: Właściwości łączników
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6d2d3d747c128cfa2afbb63ae43289e0b50519b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810070"
---
# <a name="properties-of-connectors"></a>Właściwości łączników
Łączniki reprezentują relacje domeny w wygenerowanym projektancie.

 Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Łączniki mają właściwości, które są wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślny|
|-|-|-|
|Color (Kolor)|Kolor tego łącznika.|Czarnoskórzy|
|Styl kreskowania|Styl kreskowania dla linii dla tego łącznika (Solid, kreska, kropka, DashDot, DashDotDot lub Custom).|Ciągła|
|Styl końcowy źródła|Styl końcowy dla tego łącznika (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond lub None).|Brak|
|Styl końca elementu docelowego|Styl końca elementu docelowego dla tego łącznika (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond lub None).|Brak|
|Kolor tekstu|Kolor używany dla dekoratory tekstu, które są skojarzone z tym łącznikiem.|Czarnoskórzy|
|Grubość|Grubość linii dla tego łącznika (w calach).|0,03125|
|Modyfikator dostępu|Poziom dostępu klasy ( `public` lub `internal` ).|Public|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego wygenerowanej na podstawie tego łącznika.|\<none>|
|Generuje podwójny pochodny|Jeśli `True` , zostanie wygenerowany zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma Konstruktor niestandardowy|Jeśli `True` w kodzie źródłowym zostanie podany Konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z łącznika ( `none` `abstract` lub `sealed` ).|brak|
|Podstawowy łącznik|Klasa bazowa tego łącznika.|(brak)|
|Nazwa|Nazwa tego łącznika.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, do której odnosi się ten łącznik.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Sposób definiowania etykietki narzędzia (stała, zmienna lub brak). Jeśli stała, wartość `Fixed Tooltip Text` właściwości jest używana jako etykietka narzędzia; Jeśli zmienna, a następnie etykietka narzędzia jest definiowana w kodzie niestandardowym.|\<none>|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym łącznikiem.|\<none>|
|Styl routingu|Styl używany do routingu łącznika. `Rectilinear`Łącznik sprawia, że jest to wymagane, a `Straight` Łącznik nie jest.|Rectilinear|
|Uwidoczniony kolor jako właściwość<br /><br /> Uwidoczniony styl kreskowania jako właściwość<br /><br /> Uwidoczniona grubość jako właściwość<br /><br /> Uwidacznia kolor tekstu|Jeśli `True` użytkownik może ustawić właściwość wartość dla kształtu. Aby ustawić tę opcję, kliknij prawym przyciskiem myszy definicję kształtu, a następnie kliknij pozycję **Dodaj uwidocznione**.|Fałsz|
|Opis|Służy do dokumentowania wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego łącznika.|\<none>|
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałej etykietki narzędzia.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego elementu.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))