---
title: 'CA3008: Przegląd kodu dla iniekcją XPath'
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
ms.openlocfilehash: e66b75160df0e8ecf9d33601ee383ec71cd62c4d
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018829"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008: Przegląd kodu dla iniekcją XPath

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|CheckId|CA3008|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP osiągnie zapytania XPath.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe, można w trosce o atakami polegającymi na iniekcji XPath. Konstruowanie zapytania XPath przy użyciu niezaufane dane wejściowe mogą umożliwić osobie atakującej manipulowanie złośliwie zapytanie, aby zwrócić wynik niezamierzone i potencjalnie ujawnić zawartość XML kwerendy. 

Ta zasada próbuje odnaleźć danych wejściowych z żądań HTTP, osiągając wyrażenie XPath.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, który wykonuje kwerendę XPath, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w `.editorconfig` plików.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Niektóre podejścia do ustalania XPath iniekcją obejmują:

- Nie należy tworzyć kwerendy XPath z danych wejściowych użytkownika.
- Sprawdź, czy dane wejściowe zawierają tylko z bezpiecznego zestawu znaków.
- Znak ucieczki znaki cudzysłowu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wiesz, że zweryfikowaniu danych wejściowych, bezpieczne, to można pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")
        
        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```