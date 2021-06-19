---
title: Właściwości torów
description: Dowiedz się, jak tory dzielą diagram na obszary pionowe lub poziome oraz jak można zdefiniować inne kształty, które mają być wyświetlane wewnątrz torów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c171bda2670b698297dd876a8a4403a91cd4af7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386491"
---
# <a name="properties-of-swimlanes"></a>Właściwości torów
Do diagramu można dodać tory. Tory dzielą diagram na obszary pionowe lub poziome. Możesz zdefiniować inne kształty, które mają być wyświetlane wewnątrz torów. Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i rozszerzanie [Domain-Specific języku .](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Tory mają właściwości wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślne|
|-|-|-|
|Kolor wypełnienia treści|Kolor wypełnienia dla treści torów.|Biały|
|Kolor wypełnienia nagłówka|Kolor wypełnienia nagłówka toru.|DarkGray|
|Kolor separatora|Kolor linii separatora.|LightGray|
|Styl linii separatora|Styl linii separatora ( `Solid` , , , , , lub `Dash` `Dot` `DashDot` `DashDotDot` `Custom` ).|`Dash`|
|Grubość separatora|Grubość linii separatora w calach.|0.03125|
|Kolor tekstu|Kolor używany dla dekoratorów tekstu skojarzonych z tym torysem.|Czarnoskórzy|
|Modyfikator dostępu|Poziom dostępu klasy ( `public` lub `internal` ).|Publiczne|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu, która jest generowana na podstawie tego toru.|\<none>|
|Generuje podwójne pochodne|Jeśli zostanie wygenerowana zarówno klasa bazowa, jak i klasa częściowa (w celu obsługi dostosowywania za pomocą `True` zastąpień). Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma konstruktor niestandardowy|Jeśli , w kodzie źródłowym `True` zostanie podany konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego generowanego na podstawie torów `none` (, `abstract` lub `sealed` ).|brak|
|Podstawowy tor|Klasa bazowa tego torysu.|(brak)|
|Nazwa|Nazwa tego toru.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw powiązana z tym torysem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Sposób definicji etykietki narzędzia `fixed` (, `variable` , lub `none` ). Jeśli , używana jest wartość właściwości , a jeśli wartość , etykietka narzędzia `fixed` jest `Fixed Tooltip Text` `variable` zdefiniowana w kodzie niestandardowym.|\<none>|
|Uwagi|Notatki nieformalne skojarzone z tym toryem.|\<none>|
|Wyrównanie|Wyrównanie w poziomie lub pionie.|Pionowa|
|Początkowa wysokość|Początkowa wysokość tego toru, w calach. Dotyczy tylko poziomych torów.|0|
|Szerokość początkowa|Początkowa szerokość tego toru, w calach. Dotyczy tylko pionowych torów.|0|
|Uwidacznia kolor tekstu|Jeśli ma wartość , użytkownik `True` może ustawić kolor torów w wygenerowanym projektancie. Aby to ustawić, kliknij prawym przyciskiem myszy kształt toru i kliknij polecenie **Dodaj ujawnione .**|Fałsz|
|Opis|Służy do dokumentować wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie, aby odwoływać się do tej klasy torów.|\<none>|
|Poprawiono tekst etykietki narzędzia|Tekst używany dla stałej etykietki narzędzia.|\<none>|
|Słowo kluczowe Pomocy|Słowo kluczowe używane do indeksowania pomocy F1 dla tego torysu.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))