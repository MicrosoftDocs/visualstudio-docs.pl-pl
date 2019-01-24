---
title: Praca w reguł analizy kodu edytorze zestawu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0dd83a2b2d613d6d9ef73097bca4d2f9f1c6cd39
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755881"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Praca w edytorze zestawu reguł analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z edytora zestawu reguł analizy kodu pozwala określić reguły, które są objęte niestandardowego zestawu reguł i określić akcję. Można również określić akcję do wykonania podczas analizy kodu napotka naruszenie reguły.  
  
|Akcja|Opis|  
|------------|-----------------|  
|**Ostrzeżenie**|Generuje ostrzeżenie w **lista błędów** okna.|  
|**Error**|Generuje błąd w **lista błędów** okna.|  
|**Brak**|Wyłącza regułę.|  
  
 W edytorze są wyświetlane reguły w strukturze drzewa, które grupy reguł w regule ustawić pola, które określisz. Aby dodać lub usunąć reguły z zestawu reguł, należy wykonać co najmniej jeden z następujących czynności:  
  
-   Zaznacz lub wyczyść pole wyboru w węźle grupy, aby dodać lub usunąć wszystkie reguły w grupie. Po wybraniu grupy, wszystkie reguły są ustawione na **ostrzeżenie** akcji.  
  
-   Kliknij przycisk **akcji** pole grupy, a następnie określ akcję do zastosowania do wszystkich reguł w grupie.  
  
-   Zaznacz lub wyczyść pole wyboru dla poszczególnych reguł. Po zaznaczeniu pola wyboru dla reguły ustawiono regułę ostrzeżenie akcję.  
  
## <a name="rule-set-editor-toolbar"></a>Pasek narzędzi edytora zestawu reguł  
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
  
## <a name="rule-set-fields"></a>Pola zestawu reguł  
 Zestaw reguł pól, wyświetlanie informacji o regule ustawić i może służyć do sortowania i grupowania z listy. Aby wyświetlić lub ukryć pól, kliknij przycisk **opcje kolumny** w regule zestawu narzędzi edytora i następnie zaznacz lub wyczyść pola wyboru pól, aby pokazać lub ukryć.  
  
 W poniższej tabeli opisano pola zestawu reguł.  
  
|Pole|Opis|  
|-----------|-----------------|  
|**Identyfikator**|Identyfikator reguły.|  
|**Kategoria**|Oprócz ich członkostwa w zestawy reguł reguł analizy kodu również są pogrupowane według kategorii. Aby uzyskać więcej informacji, zobacz [analiza kodu dla zarządzanego kodu ostrzeżenia](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Nazwa**|Tytuł reguły.|  
|**Namespace**|Przestrzeń nazw reguły.|  
|**Typ docelowy**|Wskazuje, czy reguła dla natywnego, zarządzanego lub bazy danych kodu.|  
|**Akcja**|Akcja podejmowana, gdy naruszenia reguły analizy kodu, uruchom.<br /><br /> **Ostrzeżenie** — generuje ostrzeżenie.<br /><br /> **Błąd** — generuje błąd.<br /><br /> **Brak** — wyłącza reguły.<br /><br /> Można edytować pole akcji. Ustawienie wartości None jest taka sama jak wyczyszczenie pola wyboru dla tej reguły.|  
|**Źródłowe zestawy reguł**|Zestaw reguł, który zawiera daną zasadę.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Sortowanie i filtrowanie zestawów reguł  
 Z nagłówków kolumn siatki zestaw reguł można sortować i filtrować zasady według wartości pola.  
  
-   Aby posortować listy zestawu reguł, kliknij nagłówek kolumny, pola, według której chcesz posortować. Jeśli zestawy reguł są grupowane, każda grupa jest sortowana indywidualnie.  
  
-   Aby filtrować zestawów reguł według wartości pola, kliknij przycisk filtru w nagłówku kolumny pola, według której chcesz filtrować. Zaznacz pole wyboru wartości, które mają być wyświetlane, a następnie wyczyść pola wyboru wartości, które chcesz ukryć.
