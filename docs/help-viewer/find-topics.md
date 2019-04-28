---
title: Wyszukaj tematy (Podgląd pomocy)
ms.date: 11/02/2017
ms.topic: conceptual
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e186bf0aa362f153ad3e6f57c39abc55c558270
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824296"
---
# <a name="how-to-search-for-topics"></a>Instrukcje: Wyszukaj tematy

Funkcja wyszukiwania pełnotekstowego, aby znaleźć wszystkie tematy, które zawierają określony wyraz. Można również dostosować i dostosowywanie wyszukiwania przy użyciu wyrażenia z symbolami wieloznacznymi, operatory logiczne i operatory wyszukiwania zaawansowanego.

Aby otworzyć **wyszukiwania** karty, wybierz polecenie **wyszukiwania** karcie **podglądu pomocy** okna, lub jeśli jesteś użytkownikiem klawiatury, wybierz opcję **Ctrl** + **E**.

## <a name="to-perform-a-full-text-search"></a>Aby wykonać wyszukiwanie pełnotekstowe

1. W polu wyszukiwania wpisz słowo, które chcesz znaleźć.

2. W zapytaniu wyszukiwania należy określić które operatory logiczne i zaawansowane wyszukiwanie do zastosowania do wyszukiwania, jeśli istnieją. Aby wyszukać wszystkie dostępne pomocy, nie należy używać operatorów.

    > [!NOTE]
    > W **Opcje podglądu** okno dialogowe, można określić dodatkowe preferencji, takich jak maksymalna liczba wyników wyszukiwania, aby wyświetlić w czasie i czy chcesz uwzględnić zawartość w języku angielskim, jeśli Twoje podstawowe ustawienia regionalne są inne niż angielskie.

3. Wybierz **Enter** klucza.

     Wyszukiwanie domyślnie zwraca maksymalnie 200 trafień i wyświetla je w obszarze wyniki wyszukiwania. Dodatkowe informacje o wersji dla każdego wyniku, może pojawić się w zależności od zawartości.

4. Aby wyświetlić temat, wybierz jego tytuł, z listy wyników.

## <a name="full-text-search-tips"></a>Porady dotyczące wyszukiwania pełnotekstowego

Można utworzyć więcej docelowych wyszukiwania, które zwracają tymi tematami, interesujące Cię, jeśli rozumiesz wpływ składni zapytania. Składnia zawiera znaki specjalne, wyrazy zastrzeżone i filtry. Ten temat zawiera wskazówki, procedury i informacje szczegółowe informacje o składni ułatwiające lepsze tworzenie zapytań.

### <a name="general-guidelines"></a>Ogólne wskazówki

Poniższa tabela zawiera niektóre podstawowe zasady i wytyczne dotyczące tworzenia zapytań wyszukiwania w Pomocy.

|Składnia|Opis|
|------------|-----------------|
|Rozróżnianie wielkości liter|Wyszukiwanie nie jest rozróżniana wielkość liter. Twórz kryteria wyszukiwania za pomocą wielkie i małe znaki. Na przykład "OLE" i "ole" zwracają takie same wyniki.|
|Kombinacje znaków|Nie można wyszukiwać tylko poszczególne litery (a – z) lub cyfry (0 – 9). Jeśli zostanie podjęta próba wyszukiwania dla niektórych słowa zastrzeżone, takie jak "i", "od" i "z" zostanie zignorowany. Aby uzyskać więcej informacji, zobacz [wyrazy ignorowane w wyszukiwaniach](#stopwords) w dalszej części tego tematu.|
|Kolejność obliczania|Zapytania wyszukiwania są przetwarzane od lewej do prawej.|

### <a name="search-syntax"></a>Składnia wyszukiwania

Jeśli określisz wyszukiwany ciąg, który zawiera wiele słów, takich jak "word1 word2", ciąg jest równoważne wprowadzeniu wyrażenia "word1 AND word2", która zwraca tylko te tematy, które zawierają wszystkie poszczególne wyrazy w wyszukiwanym ciągu.

> [!IMPORTANT]
> - Wyszukiwanie frazy nie jest obsługiwane. Jeśli określisz więcej niż jeden wyraz w wyszukiwanym ciągu zwróconego tematów będzie zawierać wszystkie wyrazy, które określiłeś, ale niekoniecznie dokładnej frazy, który określiłeś.
> - Użyj operatorów logicznych, aby określić relację między wyrazami w swojej frazy wyszukiwania. Możesz uwzględnić operatorów logicznych, takich jak AND, OR, NOT i w pobliżu, aby jeszcze bardziej Uściślij kryteria wyszukiwania. Na przykład jeśli wyszukasz "deklarowanie Unii w pobliżu" wyniki wyszukiwania zawierają tematy zawierające słowa "deklarowanie" i "union" ma więcej niż kilka słów od siebie nawzajem. Aby uzyskać więcej informacji, zobacz [operatory logiczne w wyrażeniach wyszukiwania](../help-viewer/logical-operators-search-expressions.md).

### <a name="filters"></a>Filtry

Za pomocą operatorów wyszukiwania zaawansowanego, można bardziej ograniczyć wyniki wyszukiwania. Pomoc zawiera trzy kategorie, które można użyć do filtrowania wyników wyszukiwania pełnotekstowego: Tytuł, kodu i słowo kluczowe.

### <a name="ranking-of-search-results"></a>Klasyfikacja wyników wyszukiwania

Algorytm wyszukiwania mają zastosowanie określone kryteria w celu ranga wyniki, wyższe lub niższe wyszukiwania na liście wyników. Ogólnie rzecz biorąc:

1. Zawartość, która zawiera słów kluczowych w tytule znajduje się wyżej niż zawartość, która nie.

2. Zawartość, która zawiera słów kluczowych w bliskim sąsiedztwie znajduje się wyżej niż zawartość, która nie.

3. Zawartość, która zawiera zwiększenie gęstości słów wyszukiwania znajduje się wyżej niż zawartości, który ma niższy gęstość wyszukiwanych słów.

### <a name="stopwords"> Słowa ignorowane podczas wyszukiwania (słowa ignorowane) </a>

Najczęściej występujących słów lub cyfr, które są czasem nazywane słowa ignorowane, automatycznie są pomijane podczas wyszukiwania pełnotekstowego. Na przykład jeśli możesz wyszukać frazę "przekazywania" wyniki wyszukiwania zostanie wyświetlona tematy zawierające słowo "przebiegu" ale nie "do".

## <a name="see-also"></a>Zobacz także

- [Operatory logiczne i zaawansowane](../help-viewer/logical-operators-search-expressions.md)
- [Instrukcje: Znajdowanie tematów w indeksie](../help-viewer/find-topics-index.md)
- [Instrukcje: Znajdowanie tematów w spisie treści](../help-viewer/find-topics-toc.md)
- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)