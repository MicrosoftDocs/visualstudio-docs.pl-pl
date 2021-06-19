---
title: Właściwości kształtów portu
description: Dowiedz się więcej na temat kształtów portów i sposobu używania kształtów portów do reprezentowania klas domeny w wygenerowanym projektancie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5994d2629a49757980695ca99a6d12ae21160a6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386530"
---
# <a name="properties-of-port-shapes"></a>Właściwości kształtów portu
Możesz użyć kształtów portów do reprezentowania klas domeny w wygenerowanym projektancie.

 Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i rozszerzanie [Domain-Specific języku .](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Kształty portów mają właściwości wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślne|
|-|-|-|
|Kolor wypełnienia|Kolor wypełnienia tego kształtu.|Biały|
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|Pozioma|
|Geometria|Geometria tego kształtu (prostokąt, zaokrąglony prostokąt, wielokropek lub okrąg).|Prostokąt|
|Ma domyślne punkty połączenia|W `True` przypadku obiektu kształt będzie używać górnych, dolnych, lewych i prawych punktów połączenia w wygenerowanym projektancie.|Fałsz|
|Kolor konturu|Kolor konturu tego kształtu.|Czarnoskórzy|
|Styl łącznika konturu|Styl łącznika konturu tego kształtu (Solid, Dash, Dot, DashDot, DashDotDot lub Custom).|Ciągła|
|Grubość konturu|Grubość konturu tego kształtu.|0.03125|
|Kolor tekstu|Kolor używany dla dekoratorów tekstu skojarzonych z tym kształtem.|Czarnoskórzy|
|Modyfikator dostępu|Poziom dostępu klasy ( `public` lub `internal` ).|Publiczne|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana na podstawie tego kształtu.|\<none>|
|Generuje podwójne pochodne|Jeśli zostanie wygenerowana zarówno klasa bazowa, jak i klasa częściowa (w celu obsługi dostosowywania za pomocą `True` zastąpień). Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md)|Fałsz|
|Ma konstruktor niestandardowy|Jeśli , w kodzie źródłowym `True` zostanie podany konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego generowanego na podstawie portu ( `none` lub `abstract` `sealed` ).|brak|
|Port podstawowy|Klasa bazowa tego kształtu.|(brak)|
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw powiązana z tym kształtem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Sposób definicji etykietki narzędzia (stała, zmienna lub brak). Jeśli zmienna jest stała, wartość właściwości jest używana jako etykietka narzędzia; jeśli zmienna, etykietka narzędzia jest definiowana `Fixed Tooltip Text` w kodzie niestandardowym.|brak|
|Uwagi|Notatki nieformalne skojarzone z tym kształtem.|\<none>|
|Początkowa wysokość|Początkowa wysokość tego kształtu, w calach.|1|
|Szerokość początkowa|Początkowa szerokość tego kształtu, w calach.|1.5|
|Właściwość Exposed Fill Color As<br /><br /> Tryb gradientu widocznego wypełnienia<br /><br /> Ujawniono kolor konturu jako właściwość<br /><br /> Ujawniono styl łącznika konturu jako właściwość<br /><br /> Ujawniono grubość konturu jako właściwość<br /><br /> Uwidacznia kolor tekstu|Jeśli `True` , użytkownik może ustawić podaną właściwość kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicję kształtu i kliknij polecenie **Dodaj ujawnione .**|Fałsz|
|Opis|Służy do dokumentować wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego kształtu.|\<none>|
|Naprawiono tekst etykietki narzędzia|Tekst używany dla stałej etykietki narzędzia.|\<none>|
|Słowo kluczowe Pomocy|Słowo kluczowe używane do indeksowania pomocy F1 dla tego kształtu.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))