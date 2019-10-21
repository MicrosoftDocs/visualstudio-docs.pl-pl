---
title: Porady dotyczące wyszukiwania pełnotekstowego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac683ff6e7079478d5b4e642918df4e281a53f0b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645651"
---
# <a name="full-text-search-tips"></a>Wskazówki dotyczące wyszukiwania pełnotekstowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedną z bardziej przydatnych metod lokalizowania informacji w pomocy jest przeszukiwanie pełnotekstowe. Aby udoskonalić i dostosować wyniki, musisz zrozumieć, jak składnia ma wpływ na zapytanie. Ten temat zawiera porady, procedury i szczegółowe informacje o składni, które ułatwiają lepsze tworzenie zapytań.

## <a name="full-text-search-tips"></a>Wskazówki dotyczące wyszukiwania pełnotekstowego
 Możesz utworzyć bardziej mierzone wyszukiwania, które zwracają tylko te tematy, które Cię interesują, jeśli rozumiesz, w jaki sposób pomoc interpretuje formatowanie używane w zapytaniach. Te formaty obejmują znaki specjalne, słowa zastrzeżone i filtry.

### <a name="general-guidelines"></a>Ogólne wskazówki
 Poniższa tabela zawiera podstawowe zasady i wskazówki dotyczące opracowywania zapytań wyszukiwania w pomocy.

|Składnia|Opis|
|------------|-----------------|
|Rozróżnianie wielkości liter|W wyszukiwaniu nie jest rozróżniana wielkość liter. Opracowywanie kryteriów wyszukiwania przy użyciu wielkich lub małych liter. Na przykład "OLE" i "OLE" zwracają te same wyniki.|
|Kombinacje znaków|Nie można wyszukać tylko pojedynczych liter (a – z) lub cyfr (0 – 9). Jeśli spróbujesz wyszukać określone słowa zastrzeżone, takie jak "i", "od" i "with", zostaną one zignorowane. Aby uzyskać więcej informacji, zobacz "słowa ignorowane w wyszukiwaniach (Zatrzymywanie wyrazów)" w dalszej części tego tematu.|
|Kolejność oceny|Zapytania wyszukiwania są oceniane od lewej do prawej.|

### <a name="search-syntax"></a>Składnia wyszukiwania
 Jeśli określisz ciąg wyszukiwania, który zawiera wiele słów, takich jak "word1 word2", ten ciąg jest równoznaczny z wpisaniem "word1 i word2", które zwraca tylko tematy zawierające wszystkie poszczególne wyrazy w ciągu wyszukiwania.

> [!IMPORTANT]
> 1. Wyszukiwania fraz nie są obsługiwane. W przypadku określenia więcej niż jednego wyrazu w ciągu wyszukiwania zwrócone tematy będą zawierać wszystkie słowa, które zostały określone, ale nie muszą być dokładnie określone.
>    2. Operatory logiczne służą do określania relacji między wyrazami w wyszukiwaniu. Można uwzględnić operatory logiczne, takie jak i, lub, nie i blisko, aby jeszcze bardziej zawęzić kryteria wyszukiwania. Na przykład w przypadku wyszukiwania "deklarowania blisko Unii" wyniki wyszukiwania będą zawierać tematy zawierające słowa "deklarujące" i "Union" nie więcej niż kilka wyrazów od siebie nawzajem. Aby uzyskać więcej informacji, zobacz [Operatory logiczne w wyrażeniach wyszukiwania](../ide/logical-operators-in-search-expressions.md).

### <a name="filters"></a>Filtry
 Możesz bardziej ograniczyć wyniki wyszukiwania przy użyciu operatorów wyszukiwania zaawansowanego. Pomoc zawiera trzy kategorie, których można użyć do filtrowania wyników wyszukiwania pełnotekstowego: tytuł, kod i słowo kluczowe. Aby uzyskać więcej informacji, zobacz [Zaawansowane Operatory wyszukiwania w wyrażeniach wyszukiwania](../ide/advanced-search-operators-in-search-expressions.md).

### <a name="ranking-of-search-results"></a>Klasyfikacja wyników wyszukiwania
 Algorytm wyszukiwania stosuje pewne kryteria, aby pomóc w ustalaniu rangi wyników wyszukiwania wyższych lub niższych na liście wyników. Ogólnie rzecz biorąc:

1. Zawartość obejmująca słowa wyszukiwania w tytule jest wyższa niż zawartość, która nie jest.

2. Zawartość obejmująca słowa wyszukiwania w bliskim sąsiedztwie jest wyższa niż zawartość, która nie jest.

3. Zawartość zawierająca wyższą gęstość wyrazów wyszukiwania jest wyższa niż zawartość, która ma niższą gęstość słów wyszukiwania.

### <a name="words-ignored-in-searches-stop-words"></a>Słowa ignorowane podczas wyszukiwania (Zatrzymywanie wyrazów)
 Często występujące wyrazy lub liczby, które są czasami nazywane słowami stop, są automatycznie ignorowane podczas wyszukiwania pełnotekstowego. Na przykład jeśli szukasz frazy "Przekazuj do", wyniki wyszukiwania będą wyświetlały tematy zawierające wyraz "Pass", ale nie "do".

## <a name="see-also"></a>Zobacz też
 [Lokalizowanie](../ide/locate-information.md) [operatorów logicznych informacji w wyrażeniach wyszukiwania](../ide/logical-operators-in-search-expressions.md)
