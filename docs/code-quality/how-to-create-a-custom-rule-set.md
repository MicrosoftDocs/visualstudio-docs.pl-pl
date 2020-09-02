---
title: Tworzenie niestandardowego zestawu reguł analizy kodu
ms.date: 11/02/2018
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4659efef9b233284a593fecd5c8404cb2650b0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88893271"
---
# <a name="customize-a-rule-set"></a>Dostosowywanie zestawu reguł

Można utworzyć niestandardowy zestaw reguł, który spełnia wymagania projektu dotyczące analizy kodu.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Tworzenie niestandardowego zestawu reguł na podstawie istniejącego zestawu reguł

Aby utworzyć niestandardowy zestaw reguł, można otworzyć Wbudowany zestaw reguł w **edytorze zestawu reguł**. Z tego miejsca można dodawać lub usuwać określone reguły, a także zmienić akcję, która występuje, gdy reguła zostanie naruszona &mdash; na przykład, pokazać ostrzeżenie lub błąd.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**.

2. Na stronie **Właściwości** wybierz kartę **Analiza kodu** .

::: moniker range="vs-2017"

3. Z listy rozwijanej **Uruchom ten zestaw reguł** wykonaj jedną z następujących czynności:

::: moniker-end

::: moniker range=">=vs-2019"

3. Z listy rozwijanej **aktywne reguły** wykonaj jedną z następujących czynności:

::: moniker-end

   - Wybierz zestaw reguł, który chcesz dostosować.

     \- oraz

   - Wybierz **\<Browse>** , aby określić istniejący zestaw reguł, którego nie ma na liście.

4. Wybierz pozycję **Otwórz** , aby wyświetlić reguły w edytorze zestawu reguł.

> [!NOTE]
> Jeśli masz projekt .NET Core lub .NET Standard, proces jest nieco inny, ponieważ nie ma karty właściwości **analizy kodu** . Postępuj zgodnie z instrukcjami, aby [skopiować wstępnie zdefiniowany zestaw reguł do projektu i ustawić go jako aktywny zestaw reguł](analyzer-rule-sets.md). Po skopiowaniu zestawu reguł można [go edytować w edytorze zestawu reguł programu Visual Studio](working-in-the-code-analysis-rule-set-editor.md) , otwierając go z **Eksplorator rozwiązań**.

## <a name="create-a-new-rule-set"></a>Utwórz nowy zestaw reguł

Nowy plik zestawu reguł można utworzyć przy użyciu okna dialogowego **nowy plik** :

1. Wybierz pozycję **plik**  >  **Nowy**  >  **plik**lub naciśnij **klawisze CTRL** + **N**.

2. W oknie dialogowym **nowy plik** wybierz kategorię **Ogólne** po lewej stronie, a następnie wybierz pozycję **zestaw reguł analizy kodu**.

3. Wybierz pozycję **Open** (Otwórz).

   *Nowy plik zestawu reguł zostanie* otwarty w edytorze zestawu reguł.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Tworzenie niestandardowego zestawu reguł na podstawie wielu zestawów reguł

> [!NOTE]
> Poniższa procedura nie dotyczy projektów platformy .NET Core, które nie mają karty właściwości **analizy kodu** .

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**.

2. Na stronie **Właściwości** wybierz kartę **Analiza kodu** .

::: moniker range="vs-2017"

3. Wybierz opcję **\<Choose multiple rule sets>** z **uruchamiania tego zestawu reguł**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Wybierz **\<Choose multiple rule sets>** z **aktywnych reguł**.

::: moniker-end

4. W oknie dialogowym **Dodawanie lub usuwanie zestawów reguł** wybierz zestawy reguł, które chcesz dołączyć do nowego zestawu reguł.

   ![Okno dialogowe Dodawanie lub usuwanie zestawów reguł](media/add-remove-rule-sets.png)

5. Wybierz pozycję **Zapisz jako**, wprowadź nazwę pliku *. zestawu reguł* , a następnie wybierz pozycję **Zapisz**.

   Nowy zestaw reguł zostanie wybrany na liście **Uruchom ten zestaw reguł** .

6. Wybierz pozycję **Otwórz** , aby otworzyć nowy zestaw reguł w edytorze zestawu reguł.

## <a name="rule-precedence"></a>Pierwszeństwo reguł

- Jeśli ta sama reguła zostanie wyświetlona co najmniej dwa razy w zestawie reguł z różnymi serwerami, kompilator generuje błąd. Na przykład:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Jeśli ta sama reguła zostanie wyświetlona co najmniej dwa razy w zestawie reguł o *takiej samej* ważności, w **Lista błędów**mogą pojawić się następujące ostrzeżenie:

   **CA0063: nie można załadować pliku zestawu reguł " \[ Twoje]. zestaw reguł" lub jeden z jego plików zależnych od tego zestawu. Plik jest niezgodny ze schematem zestawu reguł.**

- Jeśli zestaw reguł zawiera regułę podrzędną ustawioną przy użyciu znacznika **include** , a reguła podrzędna i nadrzędna ustawiją tę samą regułę, ale z różnymi serwerami, pierwszeństwo ma ważność w zestawie reguł nadrzędnych. Na przykład:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Nazwa i opis

Aby zmienić nazwę wyświetlaną zestawu reguł, który jest otwarty w edytorze, Otwórz okno **Właściwości** , wybierając **View**  >  **okno właściwości** widoku na pasku menu. Wprowadź nazwę wyświetlaną w polu **Nazwa** . Możesz również wprowadzić opis zestawu reguł.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz zestaw reguł, następnym krokiem jest dostosowanie reguł poprzez dodanie lub usunięcie zasad lub zmodyfikowanie ważności naruszeń reguł.

> [!div class="nextstepaction"]
> [Modyfikuj reguły w edytorze zestawu reguł](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Odwołanie zestawu reguł analizy kodu](../code-quality/rule-set-reference.md)
