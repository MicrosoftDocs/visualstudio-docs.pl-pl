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
ms.openlocfilehash: e60d0fad1262138b57f079485bc7455e55c7ec25
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841346"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007: Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP osiągnie odpowiedzi przekierowania HTTP.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe, należy zachować ostrożność, otwarte przekierowywanie luk w zabezpieczeniach. Osoba atakująca może wykorzystać luki w zabezpieczeniach otwarte przekierowywanie nadać wygląd uzasadnione adresu URL, ale przekierowania podejrzewający obiekt odwiedzający do wyłudzania informacji lub inne złośliwe strony sieci Web przy użyciu witryny sieci Web.

Ta zasada próbuje odnaleźć danych wejściowych z żądań HTTP docieranie do adresu URL przekierowania HTTP.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, który odpowiada za pomocą przekierowania HTTP, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Niektóre podejścia do ustalenia luk w zabezpieczeniach otwarte przekierowywanie obejmują:

- Nie zezwalaj użytkownikom na inicjowanie przekierowania.
- Nie zezwalaj użytkownikom na określenie dowolnej części adresu URL w przypadku przekierowania.
- Ogranicz przekierowania do wstępnie zdefiniowanych "Zezwalaj na liście" adresów URL.
- Sprawdź poprawność przekierowania adresów URL.
- Jeśli to konieczne, należy wziąć pod uwagę przy użyciu strony zastrzeżenie, gdy nastąpi przekierowanie użytkowników Twojej witryny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wiesz, że zweryfikowaniu danych wejściowych do zamierzonego adresy URL, to można pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

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
