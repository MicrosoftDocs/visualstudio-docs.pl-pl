---
title: Pomijanie naruszeń analizy kodu
ms.date: 08/27/2020
description: Dowiedz się, jak pominąć naruszenia analizy kodu w programie Visual Studio. Dowiedz się, jak używać atrybutu SuppressMessageAttribute do pomijania w źródle.
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
ms.openlocfilehash: c61803c21832367ede01817029b8d0318ac741a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859908"
---
# <a name="suppress-code-analysis-violations"></a>Pomijanie naruszeń analizy kodu

Często warto wskazać, że ostrzeżenie nie jest stosowane. Wskazuje to członkom zespołu, że kod został zrecenzowany, i że ostrzeżenie można pominąć. Pomijanie w źródle (ISS) używa atrybutu, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Aby pominąć ostrzeżenie. Ten atrybut może być umieszczony w pobliżu segmentu kodu, który wygenerował ostrzeżenie. Możesz dodać <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybut do pliku źródłowego, wpisując go w, lub możesz użyć menu skrótów na ostrzeżenie w **Lista błędów** , aby dodać je automatycznie.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Atrybut jest atrybutem warunkowym, który jest zawarty w metadanych Il zestawu kodu zarządzanego, tylko jeśli CODE_ANALYSIS symbol kompilacji jest zdefiniowany w czasie kompilacji.

W języku C++/CLI Użyj makr urzędu certyfikacji \_ pomija \_ globalnego SUPPRESS_MESSAGE komunikatu lub urzędu certyfikacji \_ \_ w pliku nagłówkowym, aby dodać atrybut.

> [!NOTE]
> Nie należy używać pominięć ze źródła w kompilacjach wydania, aby zapobiec przypadkowemu wysłaniu metadanych pomijania w źródle. Ponadto ze względu na koszt przetwarzania pomijania w źródle wydajność aplikacji może być obniżona.

::: moniker range="vs-2017"

> [!NOTE]
> W przypadku migrowania projektu do programu Visual Studio 2017 może wystąpić nagłe zaistnienie dużej liczby ostrzeżeń dotyczących analizy kodu. Jeśli nie możesz naprawić ostrzeżeń, możesz pominąć wszystkie z nich, wybierając pozycję **Analizuj**  >  **analizę kodu uruchamiania i pominąć aktywne problemy**.
>
> ![Uruchom analizę kodu i Pomiń problemy w programie Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> W przypadku migrowania projektu do programu Visual Studio 2019 może wystąpić nagłe zaistnienie dużej liczby ostrzeżeń dotyczących analizy kodu. Jeśli nie możesz naprawić ostrzeżeń, możesz pominąć wszystkie z nich, wybierając pozycję **Analizuj**  >  **kompilację i pominąć aktywne problemy**.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage — atrybut

W przypadku wybrania opcji **Pomiń** w menu kontekstowym lub kliknięciu prawym przyciskiem myszy ostrzeżenia analizy kodu w **Lista błędów** <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybut jest dodawany w kodzie lub do globalnego pliku pomijania projektu.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Atrybut ma następujący format:

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

- **Kategoria** — Kategoria, w której zdefiniowana jest reguła. Aby uzyskać więcej informacji na temat kategorii reguł analizy kodu, zobacz [ostrzeżenia dotyczące kodu zarządzanego](/dotnet/fundamentals/code-analysis/quality-rules/index).

- **CheckId** — Identyfikator reguły. Obsługa obejmuje krótką i długą nazwę identyfikatora reguły. Krótka nazwa to CAXXXX; długa nazwa to CAXXXX: FriendlyTypeName.

- **Uzasadnienie** — tekst, który jest używany do dokumentowania przyczyny pomijania wiadomości.

- **MessageID** — unikatowy identyfikator problemu dla każdego komunikatu.

- **Zakres** — element docelowy, na którym jest pomijane ostrzeżenie. Jeśli obiekt docelowy nie jest określony, zostanie ustawiony na obiekt docelowy atrybutu. Obsługiwane są następujące [zakresy](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) :

  - [`module`](#module-suppression-scope) — Ten zakres pomija ostrzeżenia względem zestawu. Jest to globalne pominięcie, które ma zastosowanie do całego projektu.

  - `resource` -(tylko[starsze FxCop](../code-quality/static-code-analysis-for-managed-code-overview.md) ) ten zakres pomija ostrzeżenia w informacjach diagnostycznych zapisywana w plikach zasobów, które są częścią modułu (zestawu). Ten zakres nie jest odczytywany/respektowany w kompilatorach/VB języka C# dla diagnostyki analizatora Roslyn, który analizuje tylko pliki źródłowe.

  - `type` — Ten zakres pomija ostrzeżenia względem typu.

  - `member` — Ten zakres pomija ostrzeżenia względem elementu członkowskiego.

  - `namespace` — Ten zakres pomija ostrzeżenia wobec samego obszaru nazw. Nie powoduje pomijania ostrzeżeń dotyczących typów w przestrzeni nazw.

  - `namespaceanddescendants` -(Wymaga kompilatora w wersji 3. x lub nowszej i programu Visual Studio 2019) ten zakres pomija ostrzeżenia w przestrzeni nazw i wszystkich jej symbolach podrzędnych. `namespaceanddescendants`Wartość jest ignorowana przez starszą analizę.

- **Target** — identyfikator, który jest używany do określenia elementu docelowego, na którym jest pomijane ostrzeżenie. Musi zawierać w pełni kwalifikowaną nazwę elementu.

Gdy widzisz ostrzeżenia w programie Visual Studio, możesz wyświetlić przykłady `SuppressMessage` przez [dodanie pomijania do globalnego pliku pomijania](../code-quality/use-roslyn-analyzers.md#suppress-violations). Atrybut pomijania i jego właściwości wymagane są wyświetlane w oknie podglądu.

## <a name="suppressmessage-usage"></a>SuppressMessage użycie

Ostrzeżenia analizy kodu są pomijane na poziomie, do którego <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> zastosowano atrybut. Na przykład atrybut może być stosowany na poziomie zestawu, modułu, typu, elementu członkowskiego lub parametru. Celem jest ścisłe sprzęganie informacji o pominięciu do kodu, w którym występuje naruszenie.

Ogólna forma pomijania obejmuje kategorię reguły i Identyfikator reguły, która zawiera opcjonalną, czytelną dla człowieka reprezentację nazwy reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Jeśli istnieją ścisłe przyczyny dotyczące minimalizowania metadanych pomijania w źródle, nazwa reguły może zostać pominięta. Kategoria reguł i jej Identyfikator reguły składają się na wystarczająco unikatowy identyfikator reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Ze względów utrzymania nie zaleca się pominięcia nazwy reguły.

## <a name="suppress-selective-violations-within-a-method-body"></a>Pomiń wybiórcze naruszenia w treści metody

Atrybuty pomijania można zastosować do metody, ale nie mogą być osadzone w treści metody. Oznacza to, że wszystkie naruszenia określonej reguły są pomijane w przypadku dodania <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu do metody.

W niektórych przypadkach może być konieczne pominięcie określonego wystąpienia naruszenia, na przykład w taki sposób, że przyszły kod nie zostanie automatycznie wykluczony z reguły analizy kodu. Niektóre reguły analizy kodu umożliwiają wykonanie tej czynności przy użyciu `MessageId` właściwości <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu. Ogólnie rzecz biorąc, starsze reguły dla naruszeń dla określonego symbolu (zmienna lokalna lub parametr) przestrzegają `MessageId` właściwości. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) jest przykładem takiej reguły. Jednak starsze reguły dla naruszeń kodu wykonywalnego (bez symboli) nie respektują `MessageId` właściwości. Dodatkowo analizatory .NET Compiler Platform ("Roslyn") nie respektują `MessageId` właściwości.

Aby pominąć określone naruszenie symbolu reguły, należy określić nazwę symbolu dla `MessageId` właściwości <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu. W poniższym przykładzie pokazano kod z dwoma naruszeniami [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) &mdash; jeden dla `name` zmiennej i jeden dla `age` zmiennej. Tylko naruszenie dla `age` symbolu jest pomijane.

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

## <a name="global-level-suppressions"></a>Pominięcia na poziomie globalnym

Narzędzie do analizy kodu zarządzanego sprawdza `SuppressMessage` atrybuty, które są stosowane na poziomie zestawu, modułu, typu, elementu członkowskiego lub parametru. Wyzwala również naruszenia zasobów i przestrzeni nazw. Te naruszenia muszą być stosowane na poziomie globalnym i są objęte zakresem i elementem przeznaczonym dla siebie. Na przykład następujący komunikat pomija naruszenie przestrzeni nazw:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Pominięcie ostrzeżenia z `namespace` zakresem powoduje pominięcie ostrzeżenia dotyczącego samego obszaru nazw. Nie powoduje pomijania ostrzeżenia o typach w przestrzeni nazw.

Wszystkie pomijanie można wyrazić, określając jawny zakres. Te pominięcia muszą się znajdować na poziomie globalnym. Nie można określić pomijania na poziomie elementu członkowskiego, dekorowania nazwy typ.

Pomijanie na poziomie globalnym jest jedynym sposobem, aby pominąć komunikaty odwołujące się do kodu generowanego przez kompilator, który nie jest mapowany do jawnie dostarczonego źródła użytkownika. Na przykład poniższy kod pomija naruszenie dla konstruktora emitującego kompilator:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` zawsze zawiera w pełni kwalifikowaną nazwę elementu.

### <a name="global-suppression-file"></a>Globalny plik pominięć

Globalny plik pominięć zachowuje pominięcia, które są pominięciami lub pominięciami na poziomie globalnym, które nie określają celu. Na przykład pominięcia dla naruszeń poziomu zestawu są przechowywane w tym pliku. Ponadto niektóre ASP.NET są przechowywane w tym pliku, ponieważ ustawienia na poziomie projektu nie są dostępne dla kodu za formularzem. Globalny plik pomijania jest tworzony i dodawany do projektu przy pierwszym zaznaczeniu opcji **w pliku pomijania projektu** **w oknie** **Lista błędów** .

### <a name="module-suppression-scope"></a>Zakres pomijania modułu

Można pominąć naruszenia jakości kodu dla całego zestawu przy użyciu zakresu **modułu** .

Na przykład następujący atrybut w pliku projektu _GlobalSuppressions_ będzie pomijał naruszenie zasad ConfigureAwait dla projektu ASP.NET Core:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

## <a name="generated-code"></a>Wygenerowany kod

Kompilatory kodu zarządzanego i narzędzia innych firm generują kod, aby ułatwić szybkie tworzenie kodu. Kod wygenerowany przez kompilator, który pojawia się w plikach źródłowych jest zwykle oznaczony przy użyciu `GeneratedCodeAttribute` atrybutu.

W przypadku analizy kodu źródłowego można pominąć komunikaty w wygenerowanym kodzie w `.editorconfig` pliku. Aby uzyskać więcej informacji, zobacz [wykluczanie wygenerowanego kodu](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code).

W przypadku starszej analizy kodu można zdecydować, czy pomijać ostrzeżenia i błędy analizy kodu dla wygenerowanego kodu. Aby uzyskać informacje na temat sposobu pomijania takich ostrzeżeń i błędów, zobacz [How to: pomijanie ostrzeżeń dla wygenerowanego kodu](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Analiza kodu jest ignorowana, `GeneratedCodeAttribute` gdy jest stosowana do całego zestawu lub jednego parametru.

## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Korzystanie z analizatorów kodu](../code-quality/use-roslyn-analyzers.md)
