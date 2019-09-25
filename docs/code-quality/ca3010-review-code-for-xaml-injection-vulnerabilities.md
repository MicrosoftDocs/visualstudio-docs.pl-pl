---
title: 'CA3010: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XAML'
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
ms.openlocfilehash: efd30a783f534d76f7f7f3fa18fd181dbe7e98a1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237239"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XAML

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP docierają <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> do metody ładowania.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufanymi danymi wejściowymi należy mieć na uwadze ataki kodu XAML. XAML jest językiem znaczników, który bezpośrednio reprezentuje Tworzenie wystąpienia obiektu i wykonywanie. Oznacza to, że elementy utworzone w języku XAML mogą korzystać z zasobów systemowych (np. dostępu do sieci i we/wy systemu plików). Jeśli osoba atakująca może kontrolować dane wejściowe do <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> wywołania metody ładowania, atakujący może wykonać kod.

Ta reguła próbuje znaleźć dane wejściowe z żądań HTTP, które <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> docierają do metody ładowania.

> [!NOTE]
> Ta reguła nie może śledzić danych między zestawami. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP, a następnie przekazuje je do innego zestawu, który ładuje kod XAML, ta reguła nie wygenerowała ostrzeżenia.

> [!NOTE]
> Istnieje konfigurowalny limit, w jaki ta reguła będzie analizować przepływ danych w ramach wywołań metod. Zobacz [konfigurację analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) , aby dowiedzieć się, jak skonfigurować limit w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Nie Ładuj niezaufanego kodu XAML.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń z tej reguły.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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
