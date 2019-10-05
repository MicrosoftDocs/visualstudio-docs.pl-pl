---
title: Pomiń ostrzeżenia analizy kodu
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 670150053053a2e556e0f111312247f243c2a8c0
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975048"
---
# <a name="suppress-code-analysis-warnings"></a>Pomiń ostrzeżenia analizy kodu

Często warto wskazać, że ostrzeżenie nie jest stosowane. Wskazuje to członkom zespołu, że kod został zrecenzowany, i że ostrzeżenie można pominąć. Pomijanie w źródle (ISS) używa atrybutu <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>, aby pominąć ostrzeżenie. Ten atrybut może być umieszczony w pobliżu segmentu kodu, który wygenerował ostrzeżenie. Możesz dodać atrybut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> do pliku źródłowego, wpisując go w, lub możesz użyć menu skrótów na ostrzeżenie w **Lista błędów** , aby dodać go automatycznie.

Atrybut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> jest atrybutem warunkowym, który jest zawarty w metadanych IL zestawu kodu zarządzanego, tylko jeśli symbol kompilacji CODE_ANALYSIS jest zdefiniowany w czasie kompilacji.

W C++programie/CLI Użyj makr CA @ NO__T-1SUPPRESS @ NO__T-2MESSAGE lub CA @ NO__T-3GLOBAL @ NO__T-4SUPPRESS_MESSAGE w pliku nagłówkowym, aby dodać atrybut.

> [!NOTE]
> Nie należy używać pominięć ze źródła w kompilacjach wydania, aby zapobiec przypadkowemu wysłaniu metadanych pomijania w źródle. Ponadto ze względu na koszt przetwarzania pomijania w źródle wydajność aplikacji może być obniżona.

::: moniker range="vs-2017"

> [!NOTE]
> W przypadku migrowania projektu do programu Visual Studio 2017 może wystąpić nagłe zaistnienie dużej liczby ostrzeżeń dotyczących analizy kodu. Jeśli nie możesz naprawić ostrzeżeń, możesz pominąć wszystkie z nich, wybierając pozycję **analizuj** > **Uruchom analizę kodu i pominąć aktywne problemy**.
>
> ![Uruchom analizę kodu i Pomiń problemy w programie Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> W przypadku migrowania projektu do programu Visual Studio 2019 może wystąpić nagłe zaistnienie dużej liczby ostrzeżeń dotyczących analizy kodu. Jeśli nie możesz naprawić ostrzeżeń, możesz pominąć wszystkie z nich, wybierając pozycję **analizuj** > **kompilacja i pominąć aktywne problemy**.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage — atrybut

Po wybraniu opcji **Pomiń** w menu kontekstowym lub kliknięciu prawym przyciskiem myszy ostrzeżenia analizy kodu w **Lista błędów**atrybut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> jest dodawany do kodu lub do globalnego pliku pomijania projektu.

Atrybut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> ma następujący format:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Właściwości tego atrybutu obejmują:

- **Kategoria** — Kategoria, w której zdefiniowana jest reguła. Aby uzyskać więcej informacji na temat kategorii reguł analizy kodu, zobacz [ostrzeżenia dotyczące kodu zarządzanego](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** — Identyfikator reguły. Obsługa obejmuje krótką i długą nazwę identyfikatora reguły. Krótka nazwa to CAXXXX; długa nazwa to CAXXXX: FriendlyTypeName.

- **Uzasadnienie** — tekst, który jest używany do dokumentowania przyczyny pomijania wiadomości.

- **MessageID** — unikatowy identyfikator problemu dla każdego komunikatu.

- **Zakres** — element docelowy, na którym jest pomijane ostrzeżenie. Jeśli obiekt docelowy nie jest określony, zostanie ustawiony na obiekt docelowy atrybutu. Obsługiwane są następujące [zakresy](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) :

  - `module`

  - `resource`

  - `type`

  - `member`

  - `namespace` — ten zakres pomija ostrzeżenia względem przestrzeni nazw. Nie powoduje pomijania ostrzeżeń dotyczących typów w przestrzeni nazw.

  - `namespaceanddescendants` — (nowość dla programu Visual Studio 2019) ten zakres pomija ostrzeżenia w przestrzeni nazw i wszystkich jej symbolach podrzędnych. Wartość `namespaceanddescendants` jest ignorowana przez starszą analizę.

- **Target** — identyfikator, który jest używany do określenia elementu docelowego, na którym jest pomijane ostrzeżenie. Musi zawierać w pełni kwalifikowaną nazwę elementu.

## <a name="suppressmessage-usage"></a>SuppressMessage użycie

Ostrzeżenia analizy kodu są pomijane na poziomie, do którego jest stosowany atrybut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. Na przykład atrybut może być stosowany na poziomie zestawu, modułu, typu, elementu członkowskiego lub parametru. Celem jest ścisłe sprzęganie informacji o pominięciu do kodu, w którym występuje naruszenie.

Ogólna forma pomijania obejmuje kategorię reguły i Identyfikator reguły, która zawiera opcjonalną, czytelną dla człowieka reprezentację nazwy reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Jeśli istnieją ścisłe przyczyny dotyczące minimalizowania metadanych pomijania w źródle, nazwa reguły może zostać pominięta. Kategoria reguł i jej Identyfikator reguły składają się na wystarczająco unikatowy identyfikator reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Ze względów utrzymania nie zaleca się pominięcia nazwy reguły.

## <a name="suppress-selective-violations-within-a-method-body"></a>Pomiń wybiórcze naruszenia w treści metody

Atrybuty pomijania można zastosować do metody, ale nie mogą być osadzone w treści metody. Oznacza to, że wszystkie naruszenia określonej reguły są pomijane, jeśli dodasz do metody atrybut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>.

W niektórych przypadkach może być konieczne pominięcie określonego wystąpienia naruszenia, na przykład w taki sposób, że przyszły kod nie zostanie automatycznie wykluczony z reguły analizy kodu. Niektóre reguły analizy kodu umożliwiają wykonanie tej czynności przy użyciu właściwości `MessageId` atrybutu <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. Ogólnie rzecz biorąc, starsze reguły dla naruszeń dla określonego symbolu (zmienna lokalna lub parametr) respektują Właściwość `MessageId`. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) jest przykładem takiej reguły. Jednak starsze reguły dla naruszeń kodu wykonywalnego (bez symboli) nie respektują właściwości `MessageId`. Ponadto .NET Compiler Platform ("Roslyn") analizatory nie respektują właściwości `MessageId`.

Aby pominąć określone naruszenie symbolu reguły, należy określić nazwę symbolu dla właściwości `MessageId` atrybutu <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. W poniższym przykładzie pokazano kod z dwoma naruszeniami [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;one dla zmiennej `name` i jeden dla zmiennej `age`. Tylko naruszenie dla symbolu `age` jest pomijane.

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

## <a name="generated-code"></a>Wygenerowany kod

Kompilatory kodu zarządzanego i narzędzia innych firm generują kod, aby ułatwić szybkie tworzenie kodu. Kod wygenerowany przez kompilator, który pojawia się w plikach źródłowych jest zwykle oznaczony atrybutem `GeneratedCodeAttribute`.

Można wybrać, czy pomijać ostrzeżenia i błędy analizy kodu dla wygenerowanego kodu. Aby uzyskać informacje na temat sposobu pomijania takich ostrzeżeń i błędów, zobacz [How: Pomiń ostrzeżenia dla wygenerowanego kodu @ no__t-0.

> [!NOTE]
> Analiza kodu ignoruje `GeneratedCodeAttribute`, gdy jest stosowany do całego zestawu lub jednego parametru.

## <a name="global-level-suppressions"></a>Pominięcia na poziomie globalnym

Narzędzie do analizy kodu zarządzanego sprawdza atrybuty `SuppressMessage`, które są stosowane na poziomie zestawu, modułu, typu, elementu członkowskiego lub parametru. Wyzwala również naruszenia zasobów i przestrzeni nazw. Te naruszenia muszą być stosowane na poziomie globalnym i są objęte zakresem i elementem przeznaczonym dla siebie. Na przykład następujący komunikat pomija naruszenie przestrzeni nazw:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Pominięcie ostrzeżenia z zakresem `namespace` powoduje pominięcie ostrzeżenia dotyczącego samego obszaru nazw. Nie powoduje pomijania ostrzeżenia o typach w przestrzeni nazw.

Wszystkie pomijanie można wyrazić, określając jawny zakres. Te pominięcia muszą się znajdować na poziomie globalnym. Nie można określić pomijania na poziomie elementu członkowskiego, dekorowania nazwy typ.

Pomijanie na poziomie globalnym jest jedynym sposobem, aby pominąć komunikaty odwołujące się do kodu generowanego przez kompilator, który nie jest mapowany do jawnie dostarczonego źródła użytkownika. Na przykład poniższy kod pomija naruszenie dla konstruktora emitującego kompilator:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` zawsze zawiera w pełni kwalifikowaną nazwę elementu.

## <a name="global-suppression-file"></a>Globalny plik pominięć

Globalny plik pominięć zachowuje pominięcia, które są pominięciami lub pominięciami na poziomie globalnym, które nie określają celu. Na przykład pominięcia dla naruszeń poziomu zestawu są przechowywane w tym pliku. Ponadto niektóre ASP.NET są przechowywane w tym pliku, ponieważ ustawienia na poziomie projektu nie są dostępne dla kodu za formularzem. Globalny plik pomijania jest tworzony i dodawany do projektu przy pierwszym zaznaczeniu opcji **w pliku pomijania projektu** **w oknie** **Lista błędów** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Korzystanie z analizatorów kodu](../code-quality/use-roslyn-analyzers.md)
