---
title: Porady dotyczące wyszukiwania pełnotekstowego | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a015aeff983979bbb8f6ddedc245c74d3fb5f77b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791711"
---
# <a name="full-text-search-tips"></a>Wskazówki dotyczące wyszukiwania pełnotekstowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jednym z bardziej użyteczne metody lokalizowania informacji w pomocy jest, wykonując wyszukiwanie pełnotekstowe. Aby dostosować i dostosować wyniki, należy zrozumieć wpływ składni zapytania. Ten temat zawiera wskazówki, procedury i informacje szczegółowe informacje o składni ułatwiające lepsze tworzenie zapytań.  
  
## <a name="full-text-search-tips"></a>Wskazówki dotyczące wyszukiwania pełnotekstowego  
 Można utworzyć więcej docelowych wyszukiwania, które zwracają odsetek czy wiesz, jak uzyskać pomoc interpretuje formatowania, które można używać tylko tych tematów w zapytaniach. Te formaty obejmują znaki specjalne, wyrazy zastrzeżone i filtry.  
  
### <a name="general-guidelines"></a>Ogólne wskazówki  
 Poniższa tabela zawiera niektóre podstawowe zasady i wytyczne dotyczące tworzenia zapytań wyszukiwania w Pomocy.  
  
|Składnia|Opis|  
|------------|-----------------|  
|Rozróżnianie wielkości liter|Wyszukiwanie nie jest rozróżniana wielkość liter. Twórz kryteria wyszukiwania za pomocą wielkie i małe znaki. Na przykład "OLE" i "ole" zwracają takie same wyniki.|  
|Kombinacje znaków|Nie można wyszukiwać tylko poszczególne litery (a – z) lub cyfry (0 – 9). Jeśli zostanie podjęta próba wyszukiwania dla niektórych słowa zastrzeżone, takie jak "i", "od" i "z" zostanie zignorowany. Aby uzyskać więcej informacji, zobacz "Słowa ignorowane podczas wyszukiwania (słowa ignorowane)" w dalszej części tego tematu.|  
|Kolejność obliczania|Zapytania wyszukiwania są przetwarzane od lewej do prawej.|  
  
### <a name="search-syntax"></a>Składnia wyszukiwania  
 Jeśli określisz wyszukiwany ciąg, który zawiera wiele słów, takich jak "word1 word2", ciąg jest równoważne wprowadzeniu wyrażenia "word1 AND word2", która zwraca tylko te tematy, które zawierają wszystkie poszczególne wyrazy w wyszukiwanym ciągu.  
  
> [!IMPORTANT]
> 1. Wyszukiwanie frazy nie jest obsługiwane. Jeśli określisz więcej niż jeden wyraz w wyszukiwanym ciągu zwróconego tematów będzie zawierać wszystkie wyrazy, które określiłeś, ale niekoniecznie dokładnej frazy, który określiłeś.  
>    2.  Użyj operatorów logicznych, aby określić relację między wyrazami w swojej frazy wyszukiwania. Możesz uwzględnić operatorów logicznych, takich jak AND, OR, NOT i w pobliżu, aby jeszcze bardziej Uściślij kryteria wyszukiwania. Na przykład jeśli wyszukasz "deklarowanie Unii w pobliżu" wyniki wyszukiwania zawierają tematy zawierające słowa "deklarowanie" i "union" ma więcej niż kilka słów od siebie nawzajem. Aby uzyskać więcej informacji, zobacz [operatory logiczne w wyrażeniach wyszukiwania](../ide/logical-operators-in-search-expressions.md).  
  
### <a name="filters"></a>Filtry  
 Za pomocą operatorów wyszukiwania zaawansowanego, można bardziej ograniczyć wyniki wyszukiwania. Pomoc zawiera trzy kategorie, które można użyć do filtrowania wyników wyszukiwania pełnotekstowego: Tytuł, kodu i słowo kluczowe. Aby uzyskać więcej informacji, zobacz [operatora wyszukiwania zaawansowanego w wyrażeniach wyszukiwania](../ide/advanced-search-operators-in-search-expressions.md).  
  
### <a name="ranking-of-search-results"></a>Klasyfikacja wyników wyszukiwania  
 Algorytm wyszukiwania mają zastosowanie określone kryteria w celu ranga wyniki, wyższe lub niższe wyszukiwania na liście wyników. Ogólnie rzecz biorąc:  
  
1.  Zawartość, która zawiera słów kluczowych w tytule znajduje się wyżej niż zawartość, która nie.  
  
2.  Zawartość, która zawiera słów kluczowych w bliskim sąsiedztwie znajduje się wyżej niż zawartość, która nie.  
  
3.  Zawartość, która zawiera zwiększenie gęstości słów wyszukiwania znajduje się wyżej niż zawartości, który ma niższy gęstość wyszukiwanych słów.  
  
### <a name="words-ignored-in-searches-stop-words"></a>Słowa ignorowane podczas wyszukiwania (słowa ignorowane)  
 Najczęściej występujących słów lub cyfr, które są czasem nazywane słowa ignorowane, automatycznie są pomijane podczas wyszukiwania pełnotekstowego. Na przykład jeśli możesz wyszukać frazę "przekazywania" wyniki wyszukiwania zostanie wyświetlona tematy zawierające słowo "przebiegu" ale nie "do".  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizowanie informacji](../ide/locate-information.md)   
 [Operatory logiczne w wyrażeniach wyszukiwania](../ide/logical-operators-in-search-expressions.md)
