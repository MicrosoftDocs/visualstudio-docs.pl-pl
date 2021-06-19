---
title: Właściwości łączników
description: Dowiedz się, że łączniki reprezentują relacje domeny w wygenerowanym projektancie i że te właściwości są służące do dostosowywania i rozszerzania języka specyficznego dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43f55aecf134bf8e4d043a4fc7f6ffa2201f8e95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390818"
---
# <a name="properties-of-connectors"></a>Właściwości łączników
Łączniki reprezentują relacje domeny w wygenerowanym projektancie.

 Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i rozszerzanie [Domain-Specific języku .](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Łączniki mają właściwości wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślne|
|-|-|-|
|Kolor|Kolor tego łącznika.|Czarnoskórzy|
|Styl łącznika|Styl łącznika dla linii dla tego łącznika (Solid, Dash, Dot, DashDot, DashDotdot lub Custom).|Ciągła|
|Styl końca źródła|Styl końca źródła dla tego łącznika (EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond lub None).|Brak|
|Docelowy styl końcowy|Docelowy styl końcowy dla tego łącznika (EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond lub None).|Brak|
|Kolor tekstu|Kolor używany dla dekoratorów tekstu skojarzonych z tym łącznikiem.|Czarnoskórzy|
|Grubość|Grubość linii dla tego łącznika mierzona w calach.|0.03125|
|Modyfikator dostępu|Poziom dostępu klasy ( `public` lub `internal` ).|Publiczne|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z tego łącznika.|\<none>|
|Generuje podwójne pochodne|Jeśli zostanie wygenerowana zarówno klasa bazowa, jak i klasa częściowa (w celu obsługi dostosowywania za pomocą `True` zastąpień). Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma konstruktor niestandardowy|Jeśli , w kodzie źródłowym `True` zostanie podany konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego wygenerowanego na podstawie łącznika ( `none` lub `abstract` `sealed` ).|brak|
|Łącznik podstawowy|Klasa bazowa tego łącznika.|(brak)|
|Nazwa|Nazwa tego łącznika.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw powiązana z tym łącznikiem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Sposób definicji etykietki narzędzia (stała, zmienna lub brak). Jeśli zmienna jest stała, wartość właściwości jest używana jako etykietka narzędzia; jeśli zmienna, etykietka narzędzia jest definiowana `Fixed Tooltip Text` w kodzie niestandardowym.|\<none>|
|Uwagi|Uwagi nieformalne skojarzone z tym łącznikiem.|\<none>|
|Styl routingu|Styl używany do kierowania łącznika. Łącznik `Rectilinear` wykonuje obrotu w prawo zgodnie z potrzebami, a łącznik `Straight` nie.|Prostoliniowy|
|Właściwość Exposed Color As<br /><br /> Ujawniono styl łącznika jako właściwość<br /><br /> Właściwość Exposed Thickness as<br /><br /> Uwidacznia kolor tekstu|Jeśli `True` , użytkownik może ustawić podaną właściwość kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicję kształtu i kliknij polecenie **Dodaj ujawnione .**|Fałsz|
|Opis|Służy do dokumentować wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego łącznika.|\<none>|
|Poprawiono tekst etykietki narzędzia|Tekst używany dla stałej etykietki narzędzia.|\<none>|
|Słowo kluczowe Pomocy|Słowo kluczowe używane do indeksowania pomocy F1 dla tego elementu.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))