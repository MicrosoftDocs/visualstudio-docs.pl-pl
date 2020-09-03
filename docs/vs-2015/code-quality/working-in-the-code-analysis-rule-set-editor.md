---
title: Praca w edytorze zestawu reguł analizy kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f25cc5a5f56c20f6a1696baa5aa3e9ee5ebdf2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621508"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Praca w edytorze zestawu reguł analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor zestawu reguł analizy kodu umożliwia określenie reguł uwzględnionych w zestawie reguł niestandardowych i określenie akcji. Możesz również określić akcję, która ma zostać podjęta, gdy analiza kodu napotka naruszenie reguły.

|Akcja|Opis|
|------------|-----------------|
|**Ostrzeżenie**|Generuje ostrzeżenie w oknie **Lista błędów** .|
|**Błąd**|Generuje błąd w oknie **Lista błędów** .|
|**Brak**|Wyłącza regułę.|

 Edytor wyświetla reguły w strukturze drzewa, które grupuje reguły według określonego pola zestawu reguł. Aby dodać lub usunąć reguły z zestawu reguł, wykonaj co najmniej jedną z następujących czynności:

- Zaznacz lub usuń zaznaczenie pola wyboru w węźle grupy, aby dodać lub usunąć wszystkie reguły w grupie. Po wybraniu grupy wszystkie reguły są ustawiane na akcję **Ostrzeżenie** .

- Kliknij pole **Akcja** w grupie, a następnie określ akcję, która ma zostać zastosowana do wszystkich reguł w grupie.

- Zaznacz lub wyczyść pole wyboru dla pojedynczej reguły. Po zaznaczeniu pola wyboru dla reguły, reguła jest ustawiana na akcję ostrzeżenia.

## <a name="rule-set-editor-toolbar"></a>Pasek narzędzi edytora zestawu reguł
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
 Pola zestawu reguł wyświetlają informacje o zestawie reguł i mogą być używane do sortowania i grupowania listy reguł. Aby wyświetlić lub ukryć pola, kliknij przycisk **Opcje kolumn** na pasku narzędzi edytora zestawu reguł, a następnie zaznacz lub wyczyść pola wyboru pól, aby pokazać lub ukryć.

 W poniższej tabeli opisano pola zestawu reguł.

|Pole|Opis|
|-----------|-----------------|
|**ID**|Identyfikator reguły.|
|**Kategoria**|Oprócz ich przynależności do zestawów reguł reguły analizy kodu są również pogrupowane według kategorii. Aby uzyskać więcej informacji, zobacz [Analiza kodu dla ostrzeżeń związanych z kodem zarządzanym](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nazwa**|Tytuł reguły.|
|**Przestrzeń nazw**|Przestrzeń nazw reguły.|
|**Typ docelowy**|Wskazuje, czy reguła dotyczy kodu natywnego, zarządzanego lub bazy danych.|
|**Akcja**|Akcja podejmowana, gdy reguła jest naruszana w przebiegu analizy kodu.<br /><br /> **Ostrzeżenie** — generuje ostrzeżenie.<br /><br /> **Błąd** — generuje błąd.<br /><br /> **Brak** — wyłącza regułę.<br /><br /> Można edytować pole akcji. Ustawienie wartości none jest takie samo jak czyszczenie pola wyboru dla reguły.|
|**Źródłowe zestawy reguł**|Zestaw reguł, który zawiera regułę.|

## <a name="sorting-and-filtering-rule-sets"></a>Sortowanie i filtrowanie zestawów reguł
 Z nagłówków kolumn siatki zestawu reguł można sortować i filtrować reguły według wartości pola.

- Aby posortować listy zestawów reguł, kliknij nagłówek kolumny pola, według którego ma zostać wykonane sortowanie. Jeśli zestawy reguł są zgrupowane, każda grupa jest sortowana pojedynczo.

- Aby odfiltrować zestawy reguł według wartości pola, kliknij przycisk Filtr w nagłówku kolumny pola, według którego chcesz filtrować. Zaznacz pola wyboru dla wartości, które chcesz wyświetlić, a następnie usuń zaznaczenie pól wyboru wartości, które chcesz ukryć.
