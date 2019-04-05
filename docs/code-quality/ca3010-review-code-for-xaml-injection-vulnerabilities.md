---
title: 'CA3010: Przejrzyj kod XAML iniekcją'
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
ms.openlocfilehash: c6d8a94dbda7cbf61ac918025aee176cb95781b2
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018897"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010: Przejrzyj kod XAML iniekcją

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Żądania HTTP potencjalnie niezaufanych danych wejściowych przypada <xref:System.Windows.Markup.XamlReader?displayProperty=fullName> metoda obciążenia.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe, można w trosce o ataki przez iniekcję kodu XAML. XAML jest językiem znaczników, który bezpośrednio reprezentuje tworzenia wystąpienia obiektu, jak i wykonywania. Oznacza to, że elementy tworzone w XAML mogą wchodzić w interakcje z zasobami systemu (na przykład sieci access i system plików we/wy). Jeśli osoba atakująca może kontrolować dane wejściowe <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> obciążenia wywołania metody, a następnie osoba atakująca może wykonać kod.

Próbuje znaleźć danych wejściowych z żądania HTTP, która będzie działać ta reguła <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> metoda obciążenia.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, który ładuje XAML, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w `.editorconfig` plików.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Nie ładuj niezaufanych XAML.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń od tej reguły.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
