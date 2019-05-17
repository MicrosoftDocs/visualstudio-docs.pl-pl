---
title: 'CA3011: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie biblioteki DLL'
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
ms.openlocfilehash: 4c9fbb4b8b11b0fce7d3e7530eef80af19b35b73
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841033"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie biblioteki DLL

|||
|-|-|
|TypeName|ReviewCodeForDllInjectionVulnerabilities|
|CheckId|CA3011|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufanych żądania HTTP, że dane wejściowe osiągnie metoda ładuje zestaw.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe, należy zachować ostrożność, ładowania niezaufanego kodu. Jeśli aplikacja sieci web ładuje niezaufanego kodu, osoba atakująca może można wstrzyknąć złośliwe biblioteki dll do procesu i wykonać złośliwy kod.

Ta zasada próbuje odnaleźć danych wejściowych z żądania HTTP, która będzie działać na metodę, która ładuje zestaw.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, który ładuje zestaw, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Niezaufane biblioteki DLL nie są ładowane z danych wejściowych użytkownika.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń od tej reguły.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;
using System.Reflection;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] rawAssembly = Convert.FromBase64String(input);
        Assembly.Load(rawAssembly);
    }
}
```

```vb
Imports System
Imports System.Reflection

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim rawAssembly As Byte() = Convert.FromBase64String(input)
        Assembly.Load(rawAssembly)
    End Sub
End Class
```
