---
title: Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia
ms.date: 04/28/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 8e25e28c2ff20a628058d5dfa71de0368fbe9249
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445610"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Użyj zestawów reguł, aby określić C++ reguły do uruchomienia

W programie Visual Studio można utworzyć i zmodyfikować niestandardowy *zestaw reguł* , aby spełniał wymagania dotyczące projektu związane z analizą kodu. Domyślne zestawy reguł są przechowywane w `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Program Visual Studio 2017 w wersji 15,7 lub nowszej:** Zestawy reguł niestandardowych można utworzyć przy użyciu dowolnego edytora tekstu i zastosować je w przypadku kompilacji w wierszu polecenia niezależnie od tego, jakiego systemu kompilacji używasz. Aby uzyskać więcej informacji, zobacz [/analyze: reguł](/cpp/build/reference/analyze-code-analysis).

Aby utworzyć niestandardowy C++ zestaw reguł w programie Visual Studio, projekt C/C++ musi być otwarty w środowisku IDE programu Visual Studio. Następnie można otworzyć standardowy zestaw reguł w edytorze zestawu reguł, a następnie dodać lub usunąć określone reguły i opcjonalnie zmienić akcję, która występuje, gdy analiza kodu ustali, że reguła została naruszona.

Aby utworzyć nowy niestandardowy zestaw reguł, Zapisz go przy użyciu nowej nazwy pliku. Niestandardowy zestaw reguł jest automatycznie przypisywany do projektu.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Aby utworzyć regułę niestandardową na podstawie jednego istniejącego zestawu reguł

1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu, a następnie wybierz **Właściwości**.

2. Na karcie **Właściwości** wybierz pozycję **Analiza kodu**.

3. Z listy rozwijanej **zestaw reguł** wykonaj jedną z następujących czynności:

   - Wybierz zestaw reguł, który chcesz dostosować.

     \- lub-

   - Wybierz **\<Browse... >** , aby określić istniejący zestaw reguł, którego nie ma na liście.

4. Wybierz pozycję **Otwórz** , aby wyświetlić reguły w edytorze zestawu reguł.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Aby zmodyfikować zestaw reguł w edytorze zestawu reguł

- Aby zmienić nazwę wyświetlaną zestawu reguł, w menu **Widok** wybierz polecenie **okno właściwości**. Wprowadź nazwę wyświetlaną w polu **Nazwa** . Zauważ, że nazwa wyświetlana może się różnić od nazwy pliku.

- Aby dodać wszystkie reguły grupy do niestandardowego zestawu reguł, zaznacz pole wyboru grupy. Aby usunąć wszystkie reguły grupy, usuń zaznaczenie pola wyboru.

- Aby dodać określoną regułę do niestandardowego zestawu reguł, zaznacz pole wyboru reguły. Aby usunąć regułę z zestawu reguł, usuń zaznaczenie pola wyboru.

- Aby zmienić akcję wykonywaną w przypadku naruszenia reguły w analizie kodu, wybierz pole **akcji** dla reguły, a następnie wybierz jedną z następujących wartości:

     **Ostrzeżenie** — generuje ostrzeżenie.

     **Błąd** — generuje błąd.
     
     **Info** — generuje komunikat.

     **Brak** — wyłącza regułę. Ta akcja jest taka sama jak usuwanie reguły z zestawu reguł.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Aby grupować, filtrować lub zmieniać pola w edytorze zestawu reguł przy użyciu paska narzędzi edytora zestawu reguł

- Aby rozwinąć reguły we wszystkich grupach, wybierz **Rozwiń wszystkie**.

- Aby zwinąć reguły we wszystkich grupach, wybierz pozycję **Zwiń wszystko**.

- Aby zmienić pole, według którego reguły są grupowane, wybierz pole z listy **Grupuj według** . Aby wyświetlić reguły niezgrupowane, wybierz **\<None >** .

- Aby dodać lub usunąć pola w kolumnach reguł, wybierz **Opcje kolumn**.

- Aby ukryć reguły, które nie mają zastosowania do bieżącego rozwiązania, wybierz **Ukryj reguły, które nie mają zastosowania do bieżącego rozwiązania**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, które są przypisane do akcji błędu, wybierz **Pokaż reguły, które mogą generować błędy analizy kodu**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, które są przypisane do akcji ostrzeżenie, wybierz **Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, do których przypisano akcję **Brak** , wybierz pozycję **Pokaż reguły, które nie są włączone**.

- Aby dodać lub usunąć zestawy reguł domyślnych firmy Microsoft do bieżącego zestawu reguł, wybierz pozycję **Dodaj lub usuń podrzędne zestawy reguł**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Aby utworzyć zestaw reguł w edytorze tekstu

Można utworzyć niestandardowy zestaw reguł w edytorze tekstów, zapisać go w dowolnej lokalizacji z rozszerzeniem `.ruleset` i zastosować go przy użyciu opcji kompilatora [/analyze: zestaw reguł](/cpp/build/reference/analyze-code-analysis) .

Poniższy przykład przedstawia podstawowy plik zestawu reguł, którego można użyć jako punktu wyjścia:

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
