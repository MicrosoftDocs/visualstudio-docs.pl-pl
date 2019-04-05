---
title: 'CA3012: Przegląd kodu dla wyrażenia regularnego iniekcją'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 114b44ec566554c81f5caf3b8ac474f9c5a75c07
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018831"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012: Przegląd kodu dla wyrażenia regularnego iniekcją

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP osiągnie wyrażenie regularne.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe, można w trosce o atakami polegającymi na iniekcji wyrażenia regularnego. Osoba atakująca może przy użyciu iniekcji wyrażenia regularnego złośliwie modyfikują wyrażenie regularne, aby wyrażenie regularne pasuje niepożądanych wyników lub aby wprowadzić wyrażenie regularne używać Procesora nadmierne skutkuje atak typu "odmowa usługi".

Ta zasada próbuje odnaleźć danych wejściowych z żądań HTTP docieranie do wyrażenia regularnego.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, który tworzy wyrażenie regularne, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w `.editorconfig` plików.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Niektóre środki zaradcze dla wstrzyknięć kodu wyrażenia regularnego obejmują:

- Zawsze używaj [dopasowania limitu czasu](/dotnet/standard/base-types/best-practices#use-time-out-values) przy użyciu wyrażeń regularnych.
- Należy unikać używania wyrażeń regularnych, w oparciu o dane wejściowe użytkownika.
- Znaki specjalne ucieczki w danych wejściowych użytkownika, wywołując <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> lub w inny sposób.
- Zezwala na tylko inne niż-znaki specjalne z danych wejściowych użytkownika.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wiesz, że używasz [dopasowania limitu czasu](/dotnet/standard/base-types/best-practices#use-time-out-values) i danych wejściowych użytkownika jest bezpłatna znaków specjalnych, można pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;
using System.Text.RegularExpressions;

public partial class WebForm : System.Web.UI.Page
{
    public string SearchableText { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string findTerm = Request.Form["findTerm"];
        Match m = Regex.Match(SearchableText, "^term=" + findTerm);
    }
}
```

```vb
Imports System
Imports System.Text.RegularExpressions

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Public Property SearchableText As String

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim findTerm As String = Request.Form("findTerm")
        Dim m As Match = Regex.Match(SearchableText, "^term=" + findTerm)
    End Sub
End Class
```
