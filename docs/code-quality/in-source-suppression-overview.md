---
title: Pomijanie ostrzeżeń analizy kodu
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
ms.openlocfilehash: 6cd61304e150da63d2d461ef364e7039789c71fc
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223094"
---
# <a name="suppress-code-analysis-warnings"></a>Pomijanie ostrzeżeń analizy kodu

Często jest to użyteczne, aby wskazać, że ostrzeżenie nie ma zastosowania. Oznacza to, aby członkowie zespołu, który został zrecenzowany przez kod i można pominąć to ostrzeżenie. Pomijanie (ISS) używa źródła <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu, aby pominąć ostrzeżenie. Ten atrybut można umieścić w pobliżu segment kodu, który wygenerował ostrzeżenia. Możesz dodać <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu do pliku źródłowego, wpisując go, lub za pomocą menu skrótów w przypadku ostrzeżenia w **lista błędów** automatycznie ją dodać.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Atrybut jest atrybutem warunkowym znajduje się w metadanych IL zestawu kodu zarządzanego, tylko wtedy, gdy zdefiniowano symbol kompilacji CODE_ANALYSIS w czasie kompilacji.

W języku C + +/ interfejsu wiersza polecenia, użyj makra urzędu certyfikacji\_POMIŃ\_wiadomości lub urzędu certyfikacji\_GLOBAL\_SUPPRESS_MESSAGE w pliku nagłówkowym, aby dodać ten atrybut.

> [!NOTE]
> Nie należy używać pominięć w źródła kompilacji do wydania, aby zapobiec przypadkowo wysyłania metadanych pomijanie w źródła. Ponadto ze względu na koszt przetwarzania pomijanie-source, może być znacznie wydajności aplikacji.

> [!NOTE]
> Jeśli migrujesz projektu programu Visual Studio 2017 lub Visual Studio 2019 r nagle może być wystąpiły z dużą liczbą ostrzeżenia analizy kodu. Ostrzeżenia te pochodzą z [analizatorów Roslyn](roslyn-analyzers-overview.md). Jeśli nie jesteś gotowy rozwiązać problem z ostrzeżeniami, można pominąć wszystkie z nich, wybierając **analizy** > **Uruchom analizę kodu i Pomiń aktywne problemy**.
>
> ![Uruchom analizę kodu i Pomiń problemy w programie Visual Studio](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage — atrybut

Po wybraniu **Pomiń** menu kontekstowe lub kliknij prawym przyciskiem myszy ostrzeżenia analizy kodu w **lista błędów**, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> w kodzie lub globalne pomijanie projektu jest dodawany atrybut plik.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Atrybut ma następujący format:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Właściwości atrybutu obejmują:

- **Kategoria** -kategorii, w którym zdefiniowano reguły. Aby uzyskać więcej informacji na temat kategorie reguł analizy kodu, zobacz [ostrzeżenia kodu zarządzanego](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** — identyfikator reguły. Obsługa obejmuje zarówno krótko- i nazwę dla identyfikatora reguły. Krótka nazwa jest CAXXXX; długa nazwa jest CAXXXX:FriendlyTypeName.

- **Uzasadnienie** — tekst, który umożliwia dokumentowanie przyczyny pomijanie komunikatu.

- **Identyfikator komunikatu** — Unikatowy identyfikator problemu dla każdego komunikatu.

- **Zakres** — element docelowy, na którym pomijane jest ostrzeżenie. Jeśli element docelowy nie zostanie określony, ustawiono element docelowy atrybutu. Obsługiwane [zakresy](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) obejmują następujące elementy:

   - `module`

   - `resource`

   - `type`

   - `member`

   - `namespace` — W tym zakresie pomija ostrzeżeń względem samej przestrzeni nazw. Go nie Pomijaj ostrzeżenia typów w przestrzeni nazw.

   - `namespaceanddescendants` -(Nowy dla programu Visual Studio 2019 r.) ten zakres pomija ostrzeżeń w przestrzeni nazw i jego elementów podrzędnych symboli. `namespaceanddescendants` Wartość jest prawidłowa tylko dla analizatory Roslyn i jest ignorowana przez analizę statyczną binarne, na podstawie programu FxCop.

- **Docelowy** — identyfikator, który służy do określania docelowych, na którym pomijane jest ostrzeżenie. Musi zawierać nazwę FQDN elementu.

## <a name="suppressmessage-usage"></a>Użycie SuppressMessage

Ostrzeżenia analizy kodu są pomijane w poziomie, do którego <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybut jest stosowany. Na przykład można zastosować atrybutu poziomie zestawu, modułu, typu, składowej lub parametru. Celem tego jest ściśle Połącz informacji pomijanie w kodzie realizowana naruszenia.

Ogólna postać pomijania zawiera kategoria reguł i identyfikatora reguły, który zawiera opcjonalne czytelny dla człowieka reprezentację nazwę reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Jeśli występują ze względu na wydajność strict do minimalizowania pomijanie w źródła metadanych, można pominąć nazwę reguły. Kategoria reguły wraz z jego identyfikator reguły stanowić wystarczająco Unikatowy identyfikator reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Ze względu na łatwość konserwacji pominięcie Nazwa reguły nie jest zalecane.

## <a name="suppress-selective-violations-within-a-method-body"></a>Pomiń selektywne naruszeń w treści metody

Pomijanie atrybuty mogą być stosowane do metody, ale nie mogą być osadzone w treści metody. Oznacza to, że wszystkie naruszenia określonej reguły są pomijane, jeśli dodasz <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu do metody.

W niektórych przypadkach można pominąć konkretnego wystąpienia naruszenia zasad, na przykład, tak aby przyszłego kodu nie są automatycznie wykluczone z reguł analizy kodu. Niektórych reguł analizy kodu można to zrobić za pomocą `MessageId` właściwość <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu. Ogólnie rzecz biorąc, starszych reguł dla naruszeń w zakresie określonego symbolu (zmienną lokalną ani parametrem) `MessageId` właściwości. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) jest przykładem takiej reguły. Jednak starsze reguły za naruszenia na kod wykonywalny (inne niż symbol) nie respektują `MessageId` właściwości. Ponadto analizatory platformie kompilatora .NET ("Roslyn") nie respektują `MessageId` właściwości.

Aby pominąć to naruszenie określonego symbolu regułę, należy określić nazwę symbolu `MessageId` właściwość <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu. W poniższym przykładzie pokazano kod za pomocą dwóch naruszeń [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;jeden dla `name` zmiennej, a drugi dla `age` zmiennej. Naruszenie dla `age` symboli jest pomijane.

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

Kompilatory kodu zarządzanego i niektóre narzędzia innych firm generowanie kodu w celu ułatwienia tworzenia szybkie kodu. Kod wygenerowany przez kompilator, który pojawia się w plikach źródłowych jest zwykle oznaczony przy użyciu `GeneratedCodeAttribute` atrybutu.

Możesz wybrać, czy pominąć ostrzeżenia analizy kodu i błędów dla wygenerowanego kodu. Aby uzyskać informacje o tym, jak pominąć tych ostrzeżeń i błędów, zobacz [jak: Pomijanie ostrzeżeń dla wygenerowanego kodu](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Analiza kodu ignoruje `GeneratedCodeAttribute` gdy jest stosowany do całego zestawu lub jeden parametr.

## <a name="global-level-suppressions"></a>Pominięcia na poziomie globalne

Narzędzie do analizy kodu zarządzanego analizuje `SuppressMessage` atrybutów, które są stosowane na poziomie zestawu, modułu, typu, składowej lub parametr. Jest również uruchamiana naruszeń względem zasobów i przestrzeni nazw. Te naruszenia musi zostać zastosowana na poziomie globalnym i są zakres i docelowe. Na przykład następujący komunikat pomija naruszenie przestrzeni nazw:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Kiedy pominąć ostrzeżenia o `namespace` zakresie go umożliwia pominięcie ostrzeżenia względem samej przestrzeni nazw. Ostrzeżenie typów w przestrzeni nazw, nie są odrzuca.

Wszelkie pomijanie może być wyrażona przez określenie zakresu jawnego. Pominięcia na te muszą znajdować się na poziomie globalnym. Nie można określić poziom elementu członkowskiego pomijanie przez urządzanie typu.

Pominięcia na poziomie globalne są jedynym sposobem na wyświetlanie komunikatów, które odwołują się do kodu generowanego przez kompilator, który nie jest mapowany na źródło jawnie podaną użytkownika. Na przykład poniższy kod powoduje pominięcie naruszenie przed konstruktorem emitowane przez kompilator:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` zawsze zawiera nazwę FQDN elementu.

## <a name="global-suppression-file"></a>Plik globalne pomijanie

Plik pominięć globalnych zachowuje ograniczeń, które są pominięcia na poziomie globalnym lub pominięcia, których nie określono elementu docelowego. Na przykład pominięcia na poziomie zestawu naruszeń są przechowywane w tym pliku. Ponadto niektóre pominięcia ASP.NET są przechowywane w ten plik, ponieważ ustawienia na poziomie projektu nie są dostępne dla kod związany z formularzem. Globalne pomijanie są tworzone i dodawane do projektu, możesz wybrać po raz pierwszy **w pliku pominięć projektu** opcji **Pomiń** polecenia w pliku **lista błędów**okna.

## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Używanie analizatorów Roslyn](../code-quality/use-roslyn-analyzers.md)