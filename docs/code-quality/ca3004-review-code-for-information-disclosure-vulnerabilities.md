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
ms.openlocfilehash: 4965c9df3c2256511b8e44de8d388a9155d0d8f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237375"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Komunikat wyjątku, ślad stosu lub Reprezentacja ciągu dociera do danych wyjściowych w sieci Web.

## <a name="rule-description"></a>Opis reguły

Odłączanie informacji o wyjątkach daje osobom atakującym wgląd w wewnętrzne dane aplikacji, co może pomóc atakującym znaleźć inne luki w zabezpieczeniach.

Ta reguła próbuje znaleźć komunikat wyjątku, ślad stosu lub ciąg reprezentujący dane wyjściowe do odpowiedzi HTTP.

> [!NOTE]
> Ta reguła nie może śledzić danych między zestawami. Na przykład, jeśli jeden zestaw przechwytuje wyjątek, a następnie przekazuje go do innego zestawu, który wyprowadza wyjątek, ta reguła nie spowoduje wygenerowania ostrzeżenia.

> [!NOTE]
> Istnieje konfigurowalny limit, w jaki ta reguła będzie analizować przepływ danych w ramach wywołań metod. Zobacz [konfigurację analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) , aby dowiedzieć się, jak skonfigurować limit w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Nie wyprowadzaj informacji o wyjątku do odpowiedzi HTTP. Zamiast tego należy podać ogólny komunikat o błędzie. Zobacz [stronę obsługa błędów OWASP](https://www.owasp.org/index.php/Error_Handling) , aby uzyskać więcej wskazówek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wiesz, że dane wyjściowe sieci Web znajduje się w granicach zaufania aplikacji i nigdy nie są narażone na zewnątrz, możesz pominąć to ostrzeżenie. Jest to rzadkie. Należy wziąć pod uwagę, że granica zaufania aplikacji i przepływy danych mogą ulec zmianie z upływem czasu.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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