---
title: 'CA3012: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia regularnego'
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
ms.openlocfilehash: 42808b3961b18a23f594800f9d0782c908c9b1ba
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237181"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia regularnego

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP docierają do wyrażenia regularnego.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufanymi danymi wejściowymi należy mieć na uwadze ataki z iniekcją wyrażeń regularnych. Osoba atakująca może użyć iniekcji wyrażenia regularnego w celu złośliwego zmodyfikowania wyrażeń regularnych, aby wyrażenie regularne pasowało do nieoczekiwanych wyników, lub aby wyrażenie regularne zużywać nadmierny procesor w wyniku ataku typu "odmowa usługi".

Ta reguła próbuje znaleźć dane wejściowe z żądań HTTP, które docierają do wyrażenia regularnego.

> [!NOTE]
> Ta reguła nie może śledzić danych między zestawami. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP, a następnie przekazuje je do innego zestawu, który tworzy wyrażenie regularne, ta reguła nie spowoduje wygenerowania ostrzeżenia.

> [!NOTE]
> Istnieje konfigurowalny limit, w jaki ta reguła będzie analizować przepływ danych w ramach wywołań metod. Zobacz [konfigurację analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) , aby dowiedzieć się, jak skonfigurować limit w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Niektóre środki zaradcze związane z iniekcją wyrażeń regularnych obejmują:

- Zawsze używaj [limitu czasu dopasowania](/dotnet/standard/base-types/best-practices#use-time-out-values) podczas używania wyrażeń regularnych.
- Unikaj używania wyrażeń regularnych na podstawie danych wejściowych użytkownika.
- Ucieczki znaków specjalnych z danych wejściowych użytkownika <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> przez wywołanie lub inną metodę.
- Zezwalaj tylko na znaki niespecjalne z danych wejściowych użytkownika.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wiesz, że używasz [limitu czasu dopasowania](/dotnet/standard/base-types/best-practices#use-time-out-values) , a dane wejściowe użytkownika są wolne od znaków specjalnych, można pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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
