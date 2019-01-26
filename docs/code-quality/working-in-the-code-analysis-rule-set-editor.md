---
title: Korzystanie z edytora zestawu reguł analizy kodu
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eea18a356eb140e3eecf779d9b5468316b4fc785
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034015"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Korzystanie z edytora zestawu reguł analizy kodu

Reguł analizy kodu ustawić edytor umożliwia określenie reguł, które znajdują się w niestandardowej regule ustawić i ustawić ważność naruszeń reguł.

W poniższej tabeli przedstawiono opcje ważności:

|Akcja (ważność)|Opis|
|-|-|
|Ostrzeżenie|Generuje ostrzeżenie w **lista błędów** a także w czasie kompilacji.|
|Błąd|Generuje błąd w **lista błędów** a także w czasie kompilacji.|
|Informacje o|Generuje komunikat **lista błędów**.|
|Hidden|Naruszenie nie jest widoczny dla użytkownika. Środowisko IDE jest powiadamiany o naruszenia, jednak.|
|Brak|Reguły są pomijane. To zachowanie jest taki sam, jakby zasada została usunięta z zestawu reguł.|

W edytorze są wyświetlane reguły w strukturze drzewa, które grupy reguł w regule ustawić pola, które określisz. Aby dodać lub usunąć reguły z zestawu reguł, należy wykonać co najmniej jeden z następujących czynności:

- Zaznacz lub wyczyść pole wyboru w węźle grupy, aby dodać lub usunąć wszystkie reguły w grupie. Po wybraniu grupy, wszystkie reguły są ustawione na **ostrzeżenie** akcji.

   > [!TIP]
   > Można zmienić, jak reguły są grupowane w **Grupuj według** listy rozwijanej.

- Kliknij przycisk **akcji** pole grupy, a następnie określ akcję do zastosowania do wszystkich reguł w grupie.

- Zaznacz lub wyczyść pole wyboru dla poszczególnych reguł. Po zaznaczeniu pola wyboru dla reguły ustawiono regułę ostrzeżenie akcję.

## <a name="toolbar"></a>Pasek narzędzi

Na pasku narzędzi edytora zestawu reguł umożliwia grupowanie, filtrowanie i wyszukiwać dane, który pojawia się w siatce zestawu reguł.

W poniższej tabeli opisano formanty na pasku narzędzi edytora zestawu reguł.

|Toolbar — formant|Opis|
|---------------------|-----------------|
|**Rozwiń wszystko**|Zawiera reguły we wszystkich grupach.|
|**Zwiń wszystko**|Ukrywa reguł we wszystkich grupach.|
|**Group By**|Określa pole, według której reguły są grupowane. Kliknij przycisk  **\<Brak >** pokazanie reguły bez grup.|
|**Opcje kolumny**|Określa reguły pola do wyświetlenia.|
|**Ukryj reguły, których nie można zastosować do bieżącego rozwiązania**|Pokazuje lub ukrywa reguły, które nie są typu docelowego jako rozwiązanie.|
|**Pokaż reguły, które mogą generować błędy analizy kodu**|Pokazuje lub ukrywa reguł, które są przypisane akcji błędu.|
|**Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**|Pokazuje lub ukrywa reguł, które są przypisane ostrzeżenie akcję.|
|**Pokaż reguły, które nie są włączone**|Pokazuje lub ukrywa reguł, które są przypisane żadne działania.|
|**Dodaj lub usuń podrzędne zestawy reguł**|Dodaje lub usuwa zasady w zestawach wybranej reguły.|
|**Wyszukaj reguły**|Wyszukuje ciąg, który należy określić wszystkie wartości pól.|

## <a name="rule-set-fields"></a>Zestaw reguł pola

Pola zestawu reguł wyświetlać informacje na temat zestawu reguł i może służyć do sortowania i grupowania z listy. Aby wyświetlić lub ukryć pól, zaznacz **opcje kolumny** w regule zestawu narzędzi edytora i następnie zaznacz lub wyczyść pola wyboru pól, aby pokazać lub ukryć.

W poniższej tabeli opisano pola zestaw reguł:

|Pole|Opis|
|-----------|-----------------|
|**Identyfikator**|Identyfikator reguły.|
|**Kategoria**|Oprócz ich członkostwa w zestawy reguł reguł analizy kodu również są pogrupowane według kategorii. Aby uzyskać więcej informacji, zobacz [ostrzeżenia analizy kodu](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nazwa**|Tytuł reguły.|
|**Namespace**|Przestrzeń nazw reguły.|
|**Typ docelowy**|Wskazuje, czy reguła dla natywnego, zarządzanego lub bazy danych kodu.|
|**Akcja**|Akcja podejmowana, gdy naruszenia reguły analizy kodu, uruchom. Możesz edytować **akcji** pola.|
|**Źródłowe zestawy reguł**|Zestaw reguł, który zawiera daną zasadę.|

## <a name="sort-and-filter-rule-sets"></a>Sortowanie i filtrowanie zestawów reguł

Z nagłówków kolumn siatki zestaw reguł można sortować i filtrować zasady według wartości pola.

- Aby posortować listy zestawu reguł, kliknij nagłówek kolumny, pola, według której chcesz posortować. Jeśli zestawy reguł są grupowane, każda grupa jest sortowana indywidualnie.

- Aby filtrować zestawów reguł według wartości pola, kliknij przycisk filtru w nagłówku kolumny pola, według której chcesz filtrować. Zaznacz pole wyboru wartości, które mają być wyświetlane, a następnie wyczyść pola wyboru wartości, które chcesz ukryć.

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md)