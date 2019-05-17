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
ms.openlocfilehash: 383011e53b14ec2cc7dd7474cd050f05295a2a73
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841471"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP osiągnie nieprzetworzone dane wyjściowe HTML.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe z żądania sieci web, można je na uwadze ataki (XSS) z użyciem skryptów między witrynami. Ataku XSS wprowadza niezaufane dane wejściowe do surowy kod HTML dane wyjściowe, dzięki czemu osoba atakująca na wykonanie złośliwych skryptów lub celowego zmodyfikować zawartość na stronie sieci web. To typowa technika jest umieszczenie `<script>` elementów przy użyciu złośliwego kodu w danych wejściowych. Aby uzyskać więcej informacji, zobacz [XSS firmy OWASP](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Ta zasada próbuje odnaleźć danych wejściowych z żądań HTTP, osiągając nieprzetworzone dane wyjściowe HTML.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, który wyprowadza surowy kod HTML, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Zamiast podawania surowy kod HTML, użyj metody lub właściwości tego pierwszego HTML — koduje dane wejściowe.
- Kodowanie HTML niezaufanych danych, po czym zostaną zwrócone surowy kod HTML.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest to bezpieczne Pomijaj ostrzeżeń dla tej reguły, jeśli:
- Wiesz, że bezpieczne znany zbiór znaków nie zawiera kodu HTML jest sprawdzana w danych wejściowych.
- Wiesz, że dane są kodowany w formacie HTML w taki sposób, nie są wykrywane przez tę regułę.

> [!NOTE]
> Ta zasada może zgłaszać wyników fałszywie dodatnich niektóre metody lub właściwości tego kodowanie HTML swoje dane wejściowe.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

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