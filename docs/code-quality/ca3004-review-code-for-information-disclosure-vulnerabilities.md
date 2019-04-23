---
title: 'CA3004: Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji'
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
ms.openlocfilehash: 82f763d9a6b1ec27975aa80054456a6bbbaeaa2b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069031"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Komunikat o wyjątku, ślad stosu lub ciąg reprezentujący osiągnie dane wyjściowe w sieci web.

## <a name="rule-description"></a>Opis reguły

Ujawnieniu informacji o wyjątku zapewnia wgląd w elementach wewnętrznych aplikacji, co może pomóc osobom atakującym znaleźć inne luki w zabezpieczeniach, aby wykorzystać osoby atakujące.

Ta zasada próbuje znaleźć komunikat o wyjątku, ślad stosu lub ciąg reprezentujący są dane wyjściowe do odpowiedzi HTTP.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw przechwytuje wyjątek i przekazuje je do innego zestawu, który generuje wyjątek, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w `.editorconfig` plików.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Nie danych wyjściowych informacje o wyjątku do odpowiedzi HTTP. Zamiast tego Podaj ogólny komunikat o błędzie. Zobacz [firmy OWASP obsługę błędów strony](https://www.owasp.org/index.php/Error_Handling) Aby uzyskać więcej wskazówek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli znasz z danych wyjściowych w sieci web znajduje się w granicy zaufania aplikacji i nigdy nie jest ujawniany poza, cieszymy się pominąć to ostrzeżenie. To jest rzadkie. Wziąć pod uwagę, że granicy zaufania aplikacji i przepływów danych może się zmieniać wraz z upływem czasu.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write(e.ToString());
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write(e.ToString())
        End Try
    End Sub
End Class
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write("An error occurred. Please try again later.");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write("An error occurred. Please try again later.")
        End Try
    End Sub
End Class
```