---
title: 'CA3007: Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania'
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
ms.openlocfilehash: 0226c0e2e66a6543b81cd8ee674a743766b65f3e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237276"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007: Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP osiągną przekierowanie odpowiedzi HTTP.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufanymi danymi wejściowymi należy mieć na uwadze luki w zabezpieczeniach dotyczące otwartych przekierowań. Osoba atakująca może wykorzystać lukę w zabezpieczeniach Open Redirect, aby użyć witryny sieci Web w celu uzyskania oryginalnego adresu URL, ale przekierować niepodejrzanego gościa do phishingu lub innej złośliwej strony sieci Web.

Ta reguła próbuje znaleźć dane wejściowe z żądań HTTP docierających do adresu URL przekierowania HTTP.

> [!NOTE]
> Ta reguła nie może śledzić danych między zestawami. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP, a następnie przekazuje je do innego zestawu, który odpowiada na Przekierowanie HTTP, ta reguła nie spowoduje wygenerowania ostrzeżenia.

> [!NOTE]
> Istnieje konfigurowalny limit, w jaki ta reguła będzie analizować przepływ danych w ramach wywołań metod. Zobacz [konfigurację analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) , aby dowiedzieć się, jak skonfigurować limit w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Niektóre podejścia do rozwiązywania luk w zabezpieczeniach Open redirect obejmują:

- Nie Zezwalaj użytkownikom na inicjowanie przekierowań.
- Nie Zezwalaj użytkownikom na określenie dowolnej części adresu URL w scenariuszu przekierowania.
- Ogranicz przekierowania do wstępnie zdefiniowanej listy dozwolonych adresów URL.
- Sprawdź poprawność adresów URL przekierowania.
- Jeśli ma to zastosowanie, rozważ użycie strony z zastrzeżeniem, gdy użytkownicy są przekierowywani z witryny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wiesz, że dane wejściowe mają być ograniczone do docelowych adresów URL, możesz pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
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
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
