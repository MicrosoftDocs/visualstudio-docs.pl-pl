---
title: Właściwości kształtów obrazu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: beb401b4056edd8f1edac5e61d02237c60504cd9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748287"
---
# <a name="properties-of-image-shapes"></a>Właściwości kształtów obrazu

Można użyć kształtów obrazu, aby określić sposób wyświetlania klas domeny w wygenerowanym projektancie. Zdefiniuj kształt obrazu, ustawiając właściwość `Image` klasy do wstępnie zdefiniowanego pliku obrazu. Obsługiwane są następujące formaty:

- . gif

- . jpg

- . jpeg

- . bmp

- . wmf

- . EMF

- . png

Domyślnie pliki zasobów projektanta, takie jak pliki obrazów, znajdują się w folderze **resources** w projekcie **DSL** .

Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

Kształty obrazów mają właściwości, które są wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślny|
|-|-|-|
|Kolor wypełnienia|Kolor wypełnienia tego kształtu.|oficjaln|
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|Układ|
|Ma domyślne punkty połączenia|Jeśli `True`, kształt będzie korzystać z górnego, dolnego, lewego i prawego punktu połączenia w wygenerowanym projektancie.|False|
|Kolor konturu|Kolor konturu tego kształtu.|gasić|
|Styl kreskowania konturu|Styl kreskowania konturu tego kształtu (pełny, kreska, kropka, DashDot, DashDotDot lub niestandardowy).|Wypełnione|
|Grubość konturu|Grubość konturu tego kształtu.|0,03125|
|Kolor tekstu|Kolor używany dla dekoratory tekstu, które są skojarzone z tym kształtem.|gasić|
|Modyfikator dostępu|Modyfikator dostępu kształtu geometrycznego (publiczny lub wewnętrzny).|Public|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z tego kształtu.|\<none >|
|Generuje podwójny pochodny|Jeśli `True`, zostaną wygenerowane zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Ma Konstruktor niestandardowy|Jeśli `True`, Konstruktor niestandardowy zostanie udostępniony w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana na podstawie kształtu obrazu (`none`, `abstract` lub `sealed`).|brak|
|Podstawowy kształt obrazu|Klasa bazowa tego kształtu.|dawaj|
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest powiązana z tym kształtem.|Bieżąca przestrzeń nazw|
|Typ etykietki narzędzia|Miejsce, w którym jest zdefiniowana etykietka narzędzia (stała, zmienna lub brak). Jeśli stała, wartość właściwości `Fixed Tooltip Text` jest używana jako etykietka narzędzia; Jeśli zmienna, wówczas etykietka narzędzia jest definiowana w kodzie niestandardowym.|brak|
|Uwagi|Nieformalne notatki, które są skojarzone z tym kształtem.|\<none >|
|Początkowa wysokość|Początkowa wysokość tego kształtu (w calach).|1|
|Szerokość początkowa|Początkowa Szerokość tego kształtu (w calach).|1,5|
|Uwidoczniony kolor wypełnienia jako właściwość<br /><br /> Uwidaczniany tryb gradientu wypełnienia<br /><br /> Uwidoczniony kolor konturu jako właściwość<br /><br /> Uwidoczniony styl kreskowania konturu jako właściwość<br /><br /> Uwidoczniona grubość konturu jako właściwość<br /><br /> Uwidacznia kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość wartość dla kształtu. Aby ustawić tę opcję, kliknij prawym przyciskiem myszy definicję kształtu, a następnie kliknij pozycję **Dodaj uwidocznione**.|False|
|Opis|Służy do dokumentowania wygenerowanego projektanta.|\<none >|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego kształtu.|\<none >|
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałej etykietki narzędzia.|\<none >|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego elementu.|\<none >|
|Obraz|Ścieżka do pliku obrazu, który jest używany dla tego kształtu.|\<none >|

## <a name="see-also"></a>Zobacz także

- [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)