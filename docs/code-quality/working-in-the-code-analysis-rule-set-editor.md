---
title: Korzystanie z edytora zestawu reguł analizy kodu
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1e53df97c0535f59d0b96e9608ad55f2cb5ab21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88893310"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Korzystanie z edytora zestawu reguł analizy kodu

Edytor zestawu reguł analizy kodu umożliwia określenie reguł uwzględnionych w zestawie reguł niestandardowych i ustawienie ważności naruszeń reguł.

W poniższej tabeli przedstawiono opcje ważności:

|Akcja (ważność)|Opis|
|-|-|
|Ostrzeżenie|Generuje ostrzeżenie w **Lista błędów** a także w czasie kompilacji.|
|Błąd|Generuje błąd w **Lista błędów** a także w czasie kompilacji.|
|Info|Generuje komunikat w **Lista błędów**.|
|Ukryty|Naruszenie nie jest widoczne dla użytkownika. Środowisko IDE jest powiadamiane jednak o naruszeniu.|
|Brak|Reguła jest pomijana. Zachowanie jest takie samo, jak w przypadku usunięcia reguły z zestawu reguł.|

Edytor wyświetla reguły w strukturze drzewa, które grupuje reguły według określonego pola zestawu reguł. Aby dodać lub usunąć reguły z zestawu reguł, wykonaj co najmniej jedną z następujących czynności:

- Zaznacz lub usuń zaznaczenie pola wyboru w węźle grupy, aby dodać lub usunąć wszystkie reguły w grupie. Po wybraniu grupy wszystkie reguły są ustawiane na akcję **Ostrzeżenie** .

   > [!TIP]
   > Można zmienić sposób grupowania reguł na liście rozwijanej **Grupuj według** .

- Kliknij pole **Akcja** w grupie, Określ akcję, która ma zostać zastosowana do wszystkich reguł w grupie.

- Zaznacz lub wyczyść pole wyboru dla pojedynczej reguły. Po zaznaczeniu pola wyboru dla reguły, reguła jest ustawiana na akcję **ostrzeżenia** .

## <a name="toolbar"></a>Pasek narzędzi

Możesz użyć paska narzędzi edytora zestawu reguł, aby grupować, filtrować i przeszukiwać dane, które pojawiają się w siatce zestawu reguł.

W poniższej tabeli opisano kontrolki na pasku narzędzi edytora zestawu reguł.

|Pasek narzędzi — formant|Opis|
|---------------------|-----------------|
|**Rozwiń wszystko**|Pokazuje reguły we wszystkich grupach.|
|**Zwiń wszystko**|Ukrywa reguły we wszystkich grupach.|
|**Grupuj według**|Określa pole, według którego są grupowane reguły. Kliknij, **\<None>** Aby wyświetlić reguły bez grup.|
|**Opcje kolumn**|Określa pola reguły do wyświetlenia.|
|**Ukryj reguły, które nie mają zastosowania do bieżącego rozwiązania**|Pokazuje lub ukrywa reguły, które nie są tego samego typu docelowego co rozwiązanie.|
|**Pokaż reguły, które mogą generować błędy analizy kodu**|Pokazuje lub ukrywa reguły, do których przypisano akcję błędu.|
|**Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**|Pokazuje lub ukrywa reguły, do których przypisano akcję ostrzeżenia.|
|**Pokaż reguły, które nie są włączone**|Pokazuje lub ukrywa reguły, do których przypisano akcję brak.|
|**Dodaj lub usuń podrzędne zestawy reguł**|Dodaje lub usuwa reguły w wybranych zestawach reguł.|
|**Reguły wyszukiwania**|Wyszukuje wszystkie wartości pól dla określonego ciągu.|

## <a name="rule-set-fields"></a>Pola zestawu reguł

Pola zestawu reguł wyświetlają informacje o zestawie reguł i mogą być używane do sortowania i grupowania listy reguł. Aby wyświetlić lub ukryć pola, zaznacz opcję **Opcje kolumn** na pasku narzędzi edytora zestawu reguł, a następnie zaznacz lub wyczyść pola wyboru pól, aby pokazać lub ukryć.

W poniższej tabeli opisano pola zestawu reguł:

|Pole|Opis|
|-----------|-----------------|
|**ID**|Identyfikator reguły.|
|**Kategoria**|Oprócz ich przynależności do zestawów reguł reguły analizy kodu są również pogrupowane według kategorii. Aby uzyskać więcej informacji, zobacz [ostrzeżenia analizy kodu](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nazwa**|Tytuł reguły.|
|**Przestrzeń nazw**|Przestrzeń nazw reguły.|
|**Typ docelowy**|Wskazuje, czy reguła dotyczy kodu natywnego, zarządzanego lub bazy danych.|
|**Akcja**|Akcja podejmowana, gdy reguła jest naruszana w przebiegu analizy kodu. Można edytować pole **akcji** .|
|**Źródłowe zestawy reguł**|Zestaw reguł, który zawiera regułę.|

## <a name="sort-and-filter-rule-sets"></a>Sortowanie i filtrowanie zestawów reguł

Z nagłówków kolumn siatki zestawu reguł można sortować i filtrować reguły według wartości pola.

- Aby posortować listy zestawu reguł, wybierz nagłówek kolumny pola, według którego ma zostać wykonane sortowanie. Jeśli zestawy reguł są zgrupowane, każda grupa jest sortowana pojedynczo.

- Aby filtrować zestawy reguł według wartości pola, wybierz przycisk Filtr w nagłówku kolumny pola, według którego chcesz filtrować. Zaznacz pola wyboru dla wartości, które chcesz wyświetlić, a następnie usuń zaznaczenie pól wyboru wartości, które chcesz ukryć.

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md)
