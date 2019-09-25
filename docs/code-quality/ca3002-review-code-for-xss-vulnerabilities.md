---
title: 'CA3002: Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami'
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
ms.openlocfilehash: 6bcf32401abdeae499097bc5187d11154e7dfc6e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237420"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP docierają do nieprzetworzonych danych wyjściowych HTML.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufanymi danymi wejściowymi z żądań sieci Web należy zastanowić się, jak ataki między środowiskami (XSS). Atak typu "XSS" powoduje dodanie niezaufanych danych wejściowych do nieprzetworzonych danych wyjściowych HTML, co umożliwia osobie atakującej wykonywanie złośliwych skryptów lub złośliwie modyfikowanie zawartości na stronie sieci Web. Typowa technika umieszcza `<script>` elementy ze złośliwym kodem w danych wejściowych. Aby uzyskać więcej informacji, zobacz [OWASP XSS](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Ta reguła próbuje znaleźć dane wejściowe z żądań HTTP osiągające nieprzetworzone dane wyjściowe HTML.

> [!NOTE]
> Ta reguła nie może śledzić danych między zestawami. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP, a następnie przekazuje je do innego zestawu, który wyprowadza nieprzetworzony kod HTML, ta reguła nie będzie generować ostrzeżenia.

> [!NOTE]
> Istnieje konfigurowalny limit, w jaki ta reguła będzie analizować przepływ danych w ramach wywołań metod. Zobacz [konfigurację analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) , aby dowiedzieć się, jak skonfigurować limit w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Zamiast wyprowadzać nieprzetworzony kod HTML, użyj metody lub właściwości, która w pierwszej kolejności HTML koduje swoje dane wejściowe.
- KOD HTML — Koduj dane niezaufane przed wprowadzeniem nieprzetworzonego kodu HTML.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły, jeśli:
- Wiadomo, że dane wejściowe są sprawdzane pod kątem znanego bezpiecznego zestawu znaków, które nie zawierają kodu HTML.
- Wiadomo, że dane są kodowane w formacie HTML w sposób niewykrywany przez tę regułę.

> [!NOTE]
> Ta reguła może zgłosić fałszywie dodatnie dla niektórych metod lub właściwości, które kod HTML zakodowuje jako dane wejściowe.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
    End Sub
End Class
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```