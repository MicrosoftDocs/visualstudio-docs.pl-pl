---
title: Pomijanie naruszeń analizy kodu
ms.date: 05/10/2021
description: Dowiedz się, jak pomijać naruszenia analizy kodu w Visual Studio. Dowiedz się, jak używać atrybutu SuppressMessageAttribute w przypadku pomijania w źródle.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: fd177a96b8789760927933fad5c0320553a72f57
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973346"
---
# <a name="suppress-code-analysis-violations"></a>Pomijanie naruszeń analizy kodu

Często warto wskazać, że ostrzeżenie nie ma zastosowania. Oznacza to członkom zespołu, że kod został przejęty i że ostrzeżenie może zostać pominięte. W tym artykule opisano różne sposoby pomijania naruszeń analizy kodu przy użyciu Visual Studio IDE.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>Pomijanie naruszeń przy użyciu pliku EditorConfig

W pliku **EditorConfig** ustaw ważność na `none` , na przykład `dotnet_diagnostic.CA1822.severity = none` . Aby dodać plik EditorConfig, zobacz [Dodawanie pliku EditorConfig do projektu](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files).

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>Pomijanie naruszeń w kodzie źródłowym

Naruszenia w kodzie można pominąć przy użyciu dyrektywy preprocesora, ostrzeżenia #pragma [(C#)](/dotnet/csharp/language-reference/preprocessor-directives.md#pragma-warning) lub dyrektywy [Disable (Visual Basic),](/dotnet/visual-basic/language-reference/directives/disable-enable.md) aby pominąć ostrzeżenie tylko dla określonego wiersza kodu. Możesz też użyć [atrybutu SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- W **edytorze kodu**

  Umieść kursor w wierszu kodu z naruszeniem i naciśnij klawisz **Ctrl** + **Period (.),** aby otworzyć menu **Szybkie** akcje. Wybierz pozycję Suppress CAXXXX (Pomiń **kod CAXXXX),** a następnie wybierz pozycję w opcji **Source (Źródło)** lub **Source (atrybut) ( Źródło (atrybut).**

  Jeśli wybierzesz **opcję w** źródle , zobaczysz podgląd dyrektywy preprocesora, która zostanie dodana do kodu.

  ::: moniker range="vs-2017"
  :::image type="content" source="media/suppress-diagnostic-from-editor.png" alt-text="Pomijanie diagnostyki z menu szybkich akcji":::
  ::: moniker-end
  ::: moniker range=">=vs-2019"
  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor.png" alt-text="Pomijanie diagnostyki z menu szybkich akcji":::

  Jeśli wybierzesz **wartość w opcji Source (atrybut)**, zobaczysz podgląd [atrybutu SuppressMessage,](#in-source-suppression-and-the-suppressmessage-attribute) który zostanie dodany do kodu.

  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor-attribute.png" alt-text="Pomijanie diagnostyki z menu szybkich akcji przy użyciu atrybutu":::
  ::: moniker-end

- Z listy **błędów**

  Wybierz reguły, które chcesz pominąć, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Pomiń**  >  **w źródle**.

  - Jeśli pominiesz  opcję **W** źródle, zostanie otwarte okno dialogowe Podgląd zmian z podglądem ostrzeżenia C# [#pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) lub Visual Basic [#Disable warning](/dotnet/visual-basic/language-reference/directives/directives) dodanego do kodu źródłowego.

    ![Podgląd dodawania #pragma w pliku kodu](media/pragma-warning-preview.png)

  W **oknie dialogowym Podgląd zmian** wybierz pozycję **Zastosuj.**

  > [!NOTE]
  > Jeśli nie widzisz opcji  menu Pomiń na Eksplorator rozwiązań **,** naruszenie prawdopodobnie pochodzi z kompilacji, a nie analizy na żywo. Na **liście błędów jest** wyświetlana diagnostyka lub naruszenia reguł zarówno z analizy kodu na żywo, jak i kompilacji. Ponieważ diagnostyka kompilacji może być nieaktualna, na przykład jeśli edytowano kod w celu naprawienia naruszenia, ale nie został ponownie skompilowany, nie można pominąć tej diagnostyki z **listy błędów**. Diagnostyka z analizy na żywo lub IntelliSense jest zawsze aktualna z bieżącymi źródłami i można ją pominąć z **listy błędów**. Aby *wykluczyć diagnostykę* kompilacji  z wybranego filtru źródła listy błędów z kompilacji **i funkcji IntelliSense** na wartość **Tylko intelliSense.** Następnie wybierz diagnostykę, którą chcesz pominąć, i kontynuuj zgodnie z wcześniejszym opisem.
  >
  > ![Filtr źródła listy błędów w Visual Studio](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>Pomijanie naruszeń przy użyciu globalnego pliku pomijania

Plik [pomijania globalnego](#global-level-suppressions) używa [atrybutu SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- Z listy **błędów wybierz** reguły, które chcesz pominąć, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Pomiń w** pliku  >  **pomijania**. Zostanie **otwarte okno dialogowe** Podgląd zmian z wyświetlonym podglądem atrybutu dodanego do pliku <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> pomijania globalnego.

  ![Podgląd dodawania atrybutu SuppressMessage do pliku pomijania](media/preview-changes-in-suppression-file.png)

- W **edytorze** kodu umieść kursor w wierszu kodu z naruszeniem, a następnie naciśnij pozycję Szybkie akcje i refaktoryzowanie **(lub** naciśnij klawisz **Ctrl** + **Period (.)**), aby otworzyć menu Szybkie akcje.  Wybierz pozycję Suppress CAXXXX (Pomiń **plik CAXXXX),** a następnie wybierz **pozycję w sekcji Suppression File (Plik pomijania).** Zostanie wyświetlony podgląd globalnego pliku [pomijania,](#global-level-suppressions) który zostanie utworzony lub zmodyfikowany.

::: moniker range=">=vs-2019"

- Z menu **Analiza** wybierz pozycję Analizuj **kompilację**  >  **i Pomiń aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "podstawowe".

::: moniker-end
::: moniker range="vs-2017"

- Z menu **Analiza** wybierz pozycję Analizuj problemy Code Analysis i Pomiń aktywne problemy na pasku menu, aby  >   pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "podstawowe".
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>Pomijanie naruszeń przy użyciu ustawień projektu

W **Eksplorator rozwiązań** otwórz właściwości projektu (kliknij prawym przyciskiem myszy projekt i wybierz polecenie Właściwości **(lub** naciśnij klawisze Alt **+ Enter**) i użyj karty **Code Analysis,** aby skonfigurować opcje. Na przykład można wyłączyć analizę kodu na żywo lub analizatory .NET.

## <a name="suppress-violations-using-a-rule-set"></a>Pomijanie naruszeń przy użyciu zestawu reguł

W **edytorze zestawu reguł** wyczyść pole wyboru obok jego nazwy lub ustaw **akcję** na **wartość Brak.**

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>Pomijanie w źródle i atrybut SuppressMessage

Pomijanie w źródle (ISS) używa <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu do pomijania ostrzeżenia. Atrybut można umieścić w pobliżu segmentu kodu, który wygenerował ostrzeżenie. Atrybut można dodać do pliku źródłowego, wpisując go, lub użyć menu skrótów w ostrzeżeniu na liście błędów, aby <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> dodać go automatycznie. 

Atrybut jest atrybutem warunkowym, który jest zawarty w metadanych IL zestawu kodu zarządzanego, tylko wtedy, CODE_ANALYSIS kompilacji jest zdefiniowany w <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> czasie kompilacji.

W języku C++/CLI użyj makra CA SUPPRESS MESSAGE lub CA GLOBAL SUPPRESS_MESSAGE w pliku \_ \_ nagłówkowym, aby dodać \_ \_ atrybut.

> [!NOTE]
> Nie należy używać pomijań w źródle w kompilacjach wydania, aby zapobiec przypadkowemu wysyłki metadanych pomijania w źródle. Ponadto ze względu na koszt przetwarzania pomijania w źródle wydajność aplikacji może ulec pogorszeniu.

::: moniker range="vs-2017"

> [!NOTE]
> W przypadku migracji projektu do Visual Studio 2017 r. może nagle wystąpić duża liczba ostrzeżeń analizy kodu. Jeśli nie chcesz naprawiać ostrzeżeń, możesz pominąć wszystkie z nich, wybierając pozycję Analizuj przebieg i  >  **Code Analysis i Pomiń aktywne problemy.**
>
> ![Uruchamianie analizy kodu i pomijanie problemów w Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019&quot;

> [!NOTE]
> W przypadku migracji projektu do Visual Studio 2019 r. może nagle wystąpić duża liczba ostrzeżeń analizy kodu. Jeśli nie chcesz naprawiać ostrzeżeń, możesz pominąć wszystkie z nich, wybierając pozycję Analizuj kompilację i Pomiń  >  **aktywne problemy.**

::: moniker-end

### <a name=&quot;suppressmessage-attribute&quot;></a>SuppressMessage — atrybut

Po wybraniu pozycji **Pomiń** w menu kontekstowym lub kliknięciu prawym przyciskiem myszy ostrzeżenia analizy kodu na liście błędów atrybut jest dodawany w kodzie lub do globalnego pliku <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> pomijania projektu.

Atrybut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> ma następujący format:

```vb
<Scope:SuppressMessage(&quot;Rule Category&quot;, &quot;Rule Id&quot;, Justification = &quot;Justification&quot;, MessageId = &quot;MessageId&quot;, Scope = &quot;Scope&quot;, Target = &quot;Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Właściwości atrybutu obejmują:

- **Kategoria** — kategoria, w której zdefiniowano regułę. Aby uzyskać więcej informacji na temat kategorii reguł analizy kodu, zobacz [Ostrzeżenia kodu zarządzanego](/dotnet/fundamentals/code-analysis/quality-rules/index).

- **CheckId** — identyfikator reguły. Obsługa obejmuje zarówno krótką, jak i długą nazwę identyfikatora reguły. Krótka nazwa to CAXXXX; długa nazwa to CAXXXX:FriendlyTypeName.

- **Uzasadnienie** — tekst używany do dokumentowania przyczyny pomijania komunikatu.

- **MessageId** — unikatowy identyfikator problemu dla każdego komunikatu.

- **Zakres** — element docelowy, w którym ostrzeżenie jest pomijane. Jeśli element docelowy nie jest określony, jest ustawiony na obiekt docelowy atrybutu. Obsługiwane [zakresy](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) obejmują następujące elementy:

  - [`module`](#module-suppression-scope) — Ten zakres pomija ostrzeżenia dotyczące zestawu. Jest to globalne pomijanie, które ma zastosowanie do całego projektu.

  - `resource` -[(tylko starsza wersja FxCop)](../code-quality/static-code-analysis-for-managed-code-overview.md) Ten zakres pomija ostrzeżenia w informacjach diagnostycznych zapisywanych w plikach zasobów, które są częścią modułu (zestawu). Ten zakres nie jest odczytywany/przestrzegany w kompilatorach C#/VB dla diagnostyki analizatora Roslyn, która analizuje tylko pliki źródłowe.

  - `type` — Ten zakres pomija ostrzeżenia dotyczące typu.

  - `member` — Ten zakres pomija ostrzeżenia dotyczące członka.

  - `namespace` — Ten zakres pomija ostrzeżenia dotyczące samej przestrzeni nazw. Nie pomija ostrzeżeń dotyczących typów w przestrzeni nazw.

  - `namespaceanddescendants` - (Wymaga kompilatora w wersji 3.x lub wyższej i Visual Studio 2019) Ten zakres pomija ostrzeżenia w przestrzeni nazw i wszystkich jej symbolach potomnych. Wartość `namespaceanddescendants` jest ignorowana przez starszą analizę.

- **Target** — identyfikator używany do określania obiektu docelowego, w którym ostrzeżenie jest pomijane. Musi zawierać w pełni kwalifikowaną nazwę elementu.

Gdy zobaczysz ostrzeżenia w Visual Studio, możesz wyświetlić przykłady, dodając pomijanie `SuppressMessage` [do globalnego pliku pomijania](../code-quality/use-roslyn-analyzers.md#suppress-violations). Atrybut pomijania i jego wymagane właściwości są wyświetlane w oknie podglądu.

### <a name="suppressmessage-usage"></a>SuppressMessage usage

Code Analysis są pomijane na poziomie, do którego <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> jest stosowany atrybut. Na przykład atrybut można zastosować na poziomie zestawu, modułu, typu, członka lub parametru. Ma to na celu ścisłe parcie informacji o pomijaniu z kodem, w którym występuje naruszenie.

Ogólna forma pomijania obejmuje kategorię reguły i identyfikator reguły, który zawiera opcjonalną, czytelną dla człowieka reprezentację nazwy reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Jeśli istnieją ścisłe przyczyny wydajności minimalizujące metadane pomijania w źródle, można pominąć nazwę reguły. Kategoria reguły i jej identyfikator reguły razem stanowią wystarczająco unikatowy identyfikator reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Ze względu na utrzymanie nie zaleca się pomijania nazwy reguły.

### <a name="suppress-selective-violations-within-a-method-body"></a>Pomijanie naruszeń selektywnych w treści metody

Atrybuty pomijania można zastosować do metody, ale nie można ich osadzić w treści metody. Oznacza to, że wszystkie naruszenia określonej reguły są pomijane w przypadku dodania <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu do metody.

W niektórych przypadkach można pominąć konkretne wystąpienie naruszenia, na przykład tak, aby przyszły kod nie był automatycznie wykluczany z reguły analizy kodu. Niektóre reguły analizy kodu umożliwiają to za pomocą `MessageId` właściwości <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu . Ogólnie rzecz biorąc, starsze reguły naruszeń określonego symbolu (zmiennej lokalnej lub parametru) respektują `MessageId` właściwość . [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) jest przykładem takiej reguły. Jednak starsze reguły naruszeń kodu wykonywalnego (bez symbolu) nie respektują `MessageId` właściwości . Ponadto .NET Compiler Platform ("Roslyn") nie respektują `MessageId` właściwości .

Aby pominąć naruszenie określonego symbolu reguły, określ nazwę symbolu `MessageId` dla właściwości <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu. W poniższym przykładzie pokazano kod z dwoma naruszeniami [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)jeden dla zmiennej i jeden &mdash; `name` dla `age` zmiennej. Pomijane jest tylko `age` naruszenie symbolu.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

### <a name="global-level-suppressions"></a>Pomijanie na poziomie globalnym

Narzędzie do analizy kodu zarządzanego sprawdza atrybuty, które są stosowane na poziomie `SuppressMessage` zestawu, modułu, typu, członka lub parametru. Ponadto wyzwała naruszenia względem zasobów i przestrzeni nazw. Te naruszenia muszą być stosowane na poziomie globalnym oraz mają zakres i są celem. Na przykład poniższy komunikat pomija naruszenie przestrzeni nazw:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Pominięcie ostrzeżenia z zakresem powoduje pominięcie `namespace` ostrzeżenia względem samej przestrzeni nazw. Nie pomija ostrzeżenia przed typami w przestrzeni nazw.

Każde pomijanie można wyrazić przez określenie jawnego zakresu. Te pomijania muszą być na poziomie globalnym. Nie można określić pomijania na poziomie członka przez dekorowanie typu.

Pomijanie na poziomie globalnym to jedyny sposób pomijania komunikatów odwołujących się do kodu generowanego przez kompilator, który nie jest mapowany na jawnie podane źródło użytkownika. Na przykład poniższy kod pomija naruszenie względem konstruktora emitowanego przez kompilator:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` Zawsze zawiera w pełni kwalifikowaną nazwę elementu.

#### <a name="global-suppression-file"></a>Plik pomijania globalnego

Plik pomijania globalnego zachowuje pomijania, które są albo pomijania na poziomie globalnym, albo pomijania, które nie określają obiektu docelowego. Na przykład w tym pliku są przechowywane pomijania naruszeń na poziomie zestawu. Ponadto niektóre ASP.NET są przechowywane w tym pliku, ponieważ ustawienia na poziomie projektu nie są dostępne dla kodu za formularzem. Globalny plik pomijania jest tworzony i dodawany do projektu przy pierwszym wybraniu  opcji **W** pliku pomijania projektu w poleceniu Pomiń w **oknie Lista** błędów.

#### <a name="module-suppression-scope"></a>Zakres pomijania modułów

Naruszenia jakości kodu dla całego zestawu można pominąć przy użyciu **zakresu** modułu.

Na przykład następujący atrybut w pliku projektu _GlobalSuppressions_ pomija naruszenie configureAwait dla projektu ASP.NET Core:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>Wygenerowany kod

Zarządzane kompilatory kodu i niektóre narzędzia innych firm generują kod, aby ułatwić szybkie tworzenie kodu. Kod generowany przez kompilator, który pojawia się w plikach źródłowych, jest zwykle oznaczony `GeneratedCodeAttribute` atrybutem .

W przypadku analizy kodu źródłowego można pominąć komunikaty w wygenerowanym kodzie w `.editorconfig` pliku. Aby uzyskać więcej informacji, zobacz [Wykluczanie wygenerowanego kodu](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code).

W przypadku starszej analizy kodu można wybrać, czy pomijać ostrzeżenia i błędy analizy kodu dla wygenerowanego kodu. Aby uzyskać informacje na temat sposobu pomijania takich ostrzeżeń i błędów, zobacz How to: Suppress Warnings for Generated Code (Jak [pominąć ostrzeżenia dla wygenerowanego kodu).](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)

> [!NOTE]
> Analiza kodu `GeneratedCodeAttribute` ignoruje, gdy jest stosowana do całego zestawu lub pojedynczego parametru.

## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Korzystanie z analizatorów kodu](../code-quality/use-roslyn-analyzers.md)
