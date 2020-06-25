---
title: Wyszukaj tematy (Podgląd pomocy)
ms.date: 11/02/2017
ms.topic: how-to
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4581d7ea0b40e2b6b519f0beafaee8744e0b46c1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284922"
---
# <a name="how-to-search-for-topics"></a>Instrukcje: wyszukiwanie tematów

Możesz użyć funkcji wyszukiwania pełnotekstowego, aby zlokalizować wszystkie tematy zawierające określony wyraz. Możesz również udoskonalać i dostosowywać wyszukiwanie przy użyciu symboli wieloznacznych, operatorów logicznych i operatorów wyszukiwania zaawansowanego.

Aby otworzyć kartę **Wyszukiwanie** , wybierz kartę **Wyszukiwanie** w oknie **podglądu pomocy** lub jeśli jesteś użytkownikiem klawiatury, wybierz pozycję **Ctrl** + **E**.

## <a name="to-perform-a-full-text-search"></a>Aby przeprowadzić wyszukiwanie pełnotekstowe

1. W polu wyszukiwania wpisz wyraz, który ma zostać znaleziony.

2. W zapytaniu wyszukiwania określ operatory wyszukiwania logicznego lub zaawansowanego, które mają być stosowane do wyszukiwania (jeśli istnieją). Aby przeszukać całą dostępną pomoc, nie używaj operatorów.

    > [!NOTE]
    > W oknie dialogowym **Opcje podglądu** można określić dodatkowe Preferencje, takie jak Maksymalna liczba wyników wyszukiwania, które mają być wyświetlane w danym momencie i czy ma być uwzględniana zawartość w języku angielskim, jeśli podstawowe ustawienia regionalne nie są w języku angielskim.

3. Wybierz klawisz **Enter** .

     Wyszukiwanie domyślnie zwraca maksymalnie 200 trafień i wyświetla je w obszarze wyników wyszukiwania. W zależności od zawartości mogą pojawić się dodatkowe informacje o wersji dla każdego wyniku.

4. Aby wyświetlić temat, wybierz jego tytuł z listy wyników.

## <a name="full-text-search-tips"></a>Porady dotyczące wyszukiwania pełnotekstowego

Możesz utworzyć bardziej mierzone wyszukiwania, które zwracają tylko te tematy, które Cię interesują, jeśli rozumiesz, jak składnia ma wpływ na zapytanie. Składnia zawiera znaki specjalne, słowa zastrzeżone i filtry. Ten temat zawiera porady, procedury i szczegółowe informacje o składni, które ułatwiają lepsze tworzenie zapytań.

### <a name="general-guidelines"></a>Ogólne wskazówki

Poniższa tabela zawiera podstawowe zasady i wskazówki dotyczące opracowywania zapytań wyszukiwania w pomocy.

|Składnia|Opis|
|------------|-----------------|
|Rozróżnianie wielkości liter|W wyszukiwaniu nie jest rozróżniana wielkość liter. Opracowywanie kryteriów wyszukiwania przy użyciu wielkich lub małych liter. Na przykład "OLE" i "OLE" zwracają te same wyniki.|
|Kombinacje znaków|Nie można wyszukać tylko pojedynczych liter (a-z) lub cyfr (0-9). Jeśli spróbujesz wyszukać określone słowa zastrzeżone, takie jak "i", "od" i "with", zostaną one zignorowane. Aby uzyskać więcej informacji, zobacz [słowa ignorowane w wyszukiwaniach w](#stopwords) dalszej części tego tematu.|
|Kolejność oceny|Zapytania wyszukiwania są oceniane od lewej do prawej.|

### <a name="search-syntax"></a>Składnia wyszukiwania

Jeśli określisz ciąg wyszukiwania, który zawiera wiele słów, takich jak "word1 word2", ten ciąg jest równoznaczny z wpisaniem "word1 i word2", które zwraca tylko tematy zawierające wszystkie poszczególne wyrazy w ciągu wyszukiwania.

> [!IMPORTANT]
> - Wyszukiwania fraz nie są obsługiwane. W przypadku określenia więcej niż jednego wyrazu w ciągu wyszukiwania zwrócone tematy będą zawierać wszystkie słowa, które zostały określone, ale nie muszą być dokładnie określone.
> - Operatory logiczne służą do określania relacji między wyrazami w wyszukiwaniu. Można uwzględnić operatory logiczne, takie jak i, lub, nie i blisko, aby jeszcze bardziej zawęzić kryteria wyszukiwania. Na przykład w przypadku wyszukiwania "deklarowania blisko Unii" wyniki wyszukiwania będą zawierać tematy zawierające słowa "deklarujące" i "Union" nie więcej niż kilka wyrazów od siebie nawzajem. Aby uzyskać więcej informacji, zobacz [Operatory logiczne w wyrażeniach wyszukiwania](../help-viewer/logical-operators-search-expressions.md).

### <a name="filters"></a>Filtry

Możesz bardziej ograniczyć wyniki wyszukiwania przy użyciu operatorów wyszukiwania zaawansowanego. Pomoc zawiera trzy kategorie, których można użyć do filtrowania wyników wyszukiwania pełnotekstowego: tytuł, kod i słowo kluczowe.

### <a name="ranking-of-search-results"></a>Klasyfikacja wyników wyszukiwania

Algorytm wyszukiwania stosuje pewne kryteria, aby pomóc w ustalaniu rangi wyników wyszukiwania wyższych lub niższych na liście wyników. Ogólnie rzecz biorąc:

1. Zawartość obejmująca słowa wyszukiwania w tytule jest wyższa niż zawartość, która nie jest.

2. Zawartość obejmująca słowa wyszukiwania w bliskim sąsiedztwie jest wyższa niż zawartość, która nie jest.

3. Zawartość zawierająca wyższą gęstość wyrazów wyszukiwania jest wyższa niż zawartość, która ma niższą gęstość słów wyszukiwania.

### <a name=""></a><a name="stopwords">Słowa ignorowane podczas wyszukiwania (Zatrzymywanie wyrazów)</a>

Często występujące wyrazy lub liczby, które są czasami nazywane słowami stop, są automatycznie ignorowane podczas wyszukiwania pełnotekstowego. Na przykład jeśli szukasz frazy "Przekazuj do", wyniki wyszukiwania będą wyświetlały tematy zawierające wyraz "Pass", ale nie "do".

## <a name="see-also"></a>Zobacz też

- [Operatory logiczne i zaawansowane](../help-viewer/logical-operators-search-expressions.md)
- [Instrukcje: Znajdowanie tematów w indeksie](../help-viewer/find-topics-index.md)
- [Instrukcje: Znajdowanie tematów w spisie treści](../help-viewer/find-topics-toc.md)
- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)