---
title: Właściwości kształtów obrazu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 20da1fc95160be69c1388f9d2986c7dc254eefa2
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967132"
---
# <a name="properties-of-image-shapes"></a>Właściwości kształtów obrazu

Można użyć kształtów obrazu, aby określić, jak klasy domeny są wyświetlane w wygenerowanym projektancie. Zdefiniuj kształt obrazu, ustawiając `Image` właściwość klasy do pliku obrazu wstępnie zdefiniowane. Obsługiwane są następujące formaty:

- .gif

- .jpg

- JPEG

- .bmp

- .wmf

- .emf

- .png

Domyślnie pliki projektanta zasobów, takich jak pliki obrazów, znajdują się w **zasobów** folderu w **Dsl** projektu.

Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

Kształty obrazu mają właściwości, które są wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślny|
|-|-|-|
|Kolor wypełnienia|Kolor wypełnienia tego kształtu.|Biały|
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|Poziome|
|Ma domyślne punkty połączenia|Jeśli `True`kształt użyje górnej, dolnej, lewej i połączenia na odpowiednie punkty w wygenerowanym projektancie.|False|
|Kolor konturu|Kolor konturu tego kształtu.|Czarny|
|Styl kreskowania konturu|Styl kreskowania konturu tego kształtu (stałe, kreski, kropki, DashDot, DashDotDot lub niestandardowy).|Stałe|
|Grubość konturu|Grubość konturu tego kształtu.|0.03125|
|Kolor tekstu|Kolor, który jest używany dla dekoratorów tekstu, które są skojarzone z tym kształtem.|Czarny|
|Modyfikator dostępu|Modyfikator dostępu elementu kształt geometryczny (wewnętrznego lub publicznego).|Public|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowany na podstawie tego kształtu.|\<Brak >|
|Generuje Double pochodne|Jeśli `True`, zostaną wygenerowane klasy podstawowej i klasy częściowej (obsługuje dostosowywania przy użyciu zastąpień). Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Ma konstruktora niestandardowego|Jeśli `True`, konstruktora niestandardowego, które będą dostępne w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modyfikator dziedziczenia|Opisuje typ dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie kształt obrazu (`none`, `abstract` lub `sealed`).|brak|
|Podstawowy kształt obrazu|Klasa bazowa tego kształtu.|(Brak)|
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym kształtem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Miejsce, gdzie został zdefiniowany etykietki narzędzia (stałe, zmienna lub brak). Jeśli następnie stałej wartości `Fixed Tooltip Text` właściwość jest używana jako etykietka narzędzia; Jeśli jest to zmienna, następnie etykietki narzędzia jest definiowana w kodzie niestandardowym.|brak|
|Uwagi|Uwagi informacyjne, które są skojarzone z tym kształtem.|\<Brak >|
|Początkowa wysokość|Początkowa wysokość tego kształtu, w calach.|1|
|Początkowa szerokość|Początkowa szerokość tego kształtu, w calach.|1.5|
|Kolor wypełnienia uwidocznione jako właściwość<br /><br /> Tryb gradientu wypełnienia narażone<br /><br /> Widoczne kolor konturu jako właściwość<br /><br /> Widoczne stylu kreskowania konturu jako właściwość<br /><br /> Grubość konturu jako właściwość widoczne<br /><br /> Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość podane kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicję kształtu, a następnie kliknij przycisk **Dodaj udostępniane**.|False|
|Opis|Umożliwia dokumentowanie wygenerowanego projektanta.|\<Brak >|
|Nazwa wyświetlana|Nazwa która będzie wyświetlana w wygenerowanym projektancie dla tego kształtu.|\<Brak >|
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla ustalonej etykietki narzędzia.|\<Brak >|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego elementu.|\<Brak >|
|Obraz|Ścieżka do pliku obrazu, który służy do tego kształtu.|\<Brak >|

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)