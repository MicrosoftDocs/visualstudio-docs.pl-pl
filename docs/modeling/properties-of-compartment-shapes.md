---
title: Właściwości kształtów przedziałów
description: Dowiedz się, że kształty przedziałów są jednym z kształtów, których można użyć do wyświetlania klasy domeny w języku specyficznym dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ec84057bfe7d49760a8f95132a30e8c927f60f0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390831"
---
# <a name="properties-of-compartment-shapes"></a>Właściwości kształtów przedziałów
Kształty przedziałów są jednym z kształtów, których można użyć do wyświetlania klasy domeny w języku specyficznym dla domeny. Przedziały można rozwijać i zwijać.

 Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i [rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Kształty przedziałów mają właściwości wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślne|
|-|-|-|
|Domyślny stan zwinięcia rozwinięcia|Jeśli `Expanded` , przedziały są wyświetlane podczas tworzenia. W `Collapsed` przypadku , nie są.|Rozwinięte|
|Kolor wypełnienia|Kolor wypełnienia tego kształtu.|Biały|
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|Pozioma|
|Geometria|Geometria tego kształtu (prostokąt lub zaokrąglony prostokąt).|Prostokąt|
|Ma domyślne punkty połączenia|W przypadku obiektu kształt będzie używać punktów połączenia `True` górnych, dolnych, lewych i prawych w wygenerowanym projektancie.|Fałsz|
|Jest widoczny nagłówek pojedynczego przedziału|Jeśli , a kształt ma jeden przedział, nagłówek `False` przedziału nie jest widoczny.|Prawda|
|Kolor konturu|Kolor konturu tego kształtu.|Czarnoskórzy|
|Styl łącznika konturu|Styl łącznika konturu tego kształtu (Solid, Dash, Dot, DashDot, DashDotDot, Custom).|Ciągła|
|Grubość konturu|Grubość konturu tego kształtu.|0.03125|
|Kolor tekstu|Kolor używany dla dekoratorów tekstu skojarzonych z tym kształtem.|Czarnoskórzy|
|Modyfikator dostępu|Poziom dostępu kształtu przedziału ( `public` lub `internal` ).|Publiczne|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana na podstawie tego kształtu przedziału|\<none>|
|Generuje podwójne pochodne|Jeśli zostanie wygenerowana zarówno klasa bazowa, jak i klasa częściowa (w celu obsługi `True` dostosowywania za pomocą zastąpień). Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma niestandardowy konstruktor|Jeśli `True` , niestandardowy konstruktor zostanie podany w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego generowanego na podstawie kształtu przedziału ( `none` `abstract` , lub `sealed` ).|Brak|
|Kształt przedziału podstawowego|Klasa bazowa tego kształtu.|(brak)|
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw powiązana z tym kształtem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Jak jest zdefiniowana etykietka narzędzia (stała, zmienna lub brak). Jeśli zmienna jest stała, wartość właściwości jest używana jako etykietka narzędzia. Jeśli zmienna, etykietka narzędzia jest definiowana `Fixed Tooltip Text` w kodzie niestandardowym.|brak|
|Uwagi|Notatki nieformalne skojarzone z tym kształtem.|\<none>|
|Wysokość początkowa|Początkowa wysokość tego kształtu, w calach. W przypadku kształtów przedziałów jest to tylko wysokość sekcji nagłówka i nie można zmienić jej rozmiaru.|1|
|Szerokość początkowa|Początkowa szerokość tego kształtu, w calach.|1.5|
|Ujawniono właściwość Kolor wypełnienia jako<br /><br /> Ujawniony tryb gradientu wypełnienia<br /><br /> Ujawniono kolor konturu jako właściwość<br /><br /> Ujawniono styl łącznika konturu jako właściwość<br /><br /> Ujawniono grubość konturu jako właściwość<br /><br /> Uwidacznia kolor tekstu|Jeśli `True` , użytkownik może ustawić podaną właściwość kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicję kształtu i kliknij polecenie **Dodaj ujawnione**.|Fałsz|
|Opis|Służy do dokumentować wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego kształtu.|\<none>|
|Naprawiono tekst etykietki narzędzia|Tekst używany dla stałej etykietki narzędzia.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe używane do indeksowania pomocy F1 dla tego kształtu.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))