---
title: Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia
ms.date: 04/28/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: d4d7dfc1f010b860653edbe14fa7af9050bddba4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820376"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia

W programie Visual Studio, można tworzyć i modyfikować niestandardowego *zestaw reguł* do potrzeb określonego projektu skojarzony z analizy kodu. Domyślne zestawy reguł są przechowywane w `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 w wersji 15.7 lub nowszej** można Tworzenie niestandardowych zestawów reguł za pomocą dowolnego tekstu edytora i zastosować je w kompilacji z wiersza polecenia niezależnie od tego, co skompilować używanego systemu. Aby uzyskać więcej informacji, zobacz [/ analyze: ruleset](/cpp/build/reference/analyze-code-analysis).

Aby utworzyć niestandardową regułę języka C++ w programie Visual Studio, projekt języka C/C++, należy otworzyć w programie Visual Studio IDE. Można następnie otwórz zestaw standardowych reguł w edytorze zestawu reguł i następnie dodaj lub usuń określone reguły i opcjonalnie Zmień akcję wykonywaną podczas analizy kodu Określa, że reguły zostały naruszone.

Aby utworzyć nową regułę niestandardową zestawu, zapisz go przy użyciu nowej nazwy pliku. Niestandardowego zestawu reguł jest przypisywany do projektu.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Aby utworzyć niestandardową regułę z jednego istniejącego zestawu reguł

1. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.

2. Na **właściwości** kartę, wybrać **analizy kodu**.

3. W **zestaw reguł** listy rozwijanej, wykonaj jedną z następujących czynności:

   - Wybierz zestaw reguł, który chcesz dostosować.

     \- lub —

   - Wybierz  **\<Przeglądaj … >** do określenia zestawu istniejącą regułę, która nie jest na liście.

4. Wybierz **Otwórz** reguły są wyświetlane w edytorze zestawu reguł.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Aby zmodyfikować regułę ustawić w edytorze zestawu reguł

- Aby zmienić nazwę wyświetlaną zestawu reguł na **widoku** menu, wybierz **okno właściwości**. Wprowadź nazwę wyświetlaną w **nazwa** pole. Należy zauważyć, że nazwa wyświetlana może się różnić od nazwy pliku.

- Aby dodać zasady grupy do niestandardowego zestawu reguł, zaznacz pole wyboru grupy. Aby usunąć wszystkie zasady grupy, wyczyść pole wyboru.

- Aby dodać daną regułę do niestandardowego zestawu reguł, zaznacz pole wyboru reguły. Aby usunąć regułę z zestawu reguł, wyczyść pole wyboru.

- Aby zmienić akcję wykonywaną, gdy naruszenia reguły analizy kodu, wybierz **akcji** pola dla tej reguły, a następnie wybierz jedno z następujących wartości:

     **Ostrzegaj** — generuje ostrzeżenie.

     **Błąd** — generuje błąd.

     **Brak** — wyłącza reguły. Ta akcja jest taka sama jak usunięcie reguły z zestawu reguł.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Do grupy, filtrowanie lub zmiany pól w edytorze zestawu reguł za pomocą paska narzędzi edytora zestawu reguł

- Aby rozszerzyć reguły we wszystkich grupach, wybierz **Rozwiń wszystko**.

- Aby zwinąć reguł we wszystkich grupach, wybierz opcję **Zwiń wszystkie**.

- Aby zmienić pola, które reguły są grupowane według, wybierz pole z **Group By** listy. Aby wyświetlić reguły niezgrupowane, wybierz  **\<Brak >** .

- Aby dodać lub usunąć pola w kolumnach regułę, wybierz opcję **opcje kolumny**.

- Aby ukryć reguł, które nie mają zastosowanie do bieżącego rozwiązania, wybierz opcję **Ukryj reguł, które nie mają zastosowanie do bieżącego rozwiązania**.

- Aby przełączać się między pokazywaniu i ukrywaniu reguł, które są przypisane akcji błędu, wybierz opcję **Pokaż reguły, które mogą generować błędy analizy kodu**.

- Aby przełączać się między pokazywaniu i ukrywaniu reguł, które są przypisane ostrzeżenie akcję, wybierz opcję **Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**.

- Aby przełączać się między pokazywaniu i ukrywaniu reguł, które są przypisane **Brak** akcji, wybierz **Pokaż reguły, które nie są włączone**.

- Aby dodać lub usunąć domyślnej reguły ustawia bieżący zestaw reguł firmy Microsoft, wybierz opcję **apletu Dodaj lub usuń podrzędne zestawy reguł**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Aby utworzyć zestaw reguł w edytorze tekstu

Można utworzyć niestandardowego zestawu reguł w tekście edytora, zapisz go w dowolnej lokalizacji z `.ruleset` rozszerzenia i stosuje się przy użyciu [/ analyze: ruleset](/cpp/build/reference/analyze-code-analysis) — opcja kompilatora.

Poniższy przykład pokazuje, że plik, który służy jako punkt początkowy zestaw podstawowych reguł:

::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end
