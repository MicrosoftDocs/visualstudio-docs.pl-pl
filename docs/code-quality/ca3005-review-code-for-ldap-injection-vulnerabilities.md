---
title: 'CA3005: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie protokołu LDAP'
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
ms.openlocfilehash: 38c28153fa513c4f4db5b3a7833d279674f66734
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110378"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie protokołu LDAP

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP osiągnie instrukcję LDAP.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe, można w trosce o atakami polegającymi na iniekcji Lightweight Directory Access protokołu (LDAP). Osoba atakująca może potencjalnie uruchamiać złośliwe instrukcje LDAP katalogów informacji. Aplikacje, które używają danych wejściowych użytkownika do konstruowania dynamicznych instrukcji LDAP, aby uzyskać dostęp do katalogu usług są szczególnie narażone.

Ta zasada próbuje odnaleźć danych wejściowych z żądań HTTP w osiągnięciu instrukcji LDAP.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, który wykonuje instrukcję LDAP, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w `.editorconfig` plików.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Dla kontrolowanej przez użytkownika części instrukcji LDAP należy wziąć pod uwagę jedną z:
- Zezwalaj na bezpieczne listę znaków specjalnych innych niż.
- Nie zezwalaj na znaki specjalne
- Znaki specjalne ucieczki.

Zobacz [firmy OWASP LDAP iniekcji zapobiegania da się oszukać arkusza](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) Aby uzyskać więcej wskazówek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli znasz z danych wejściowych zostało zweryfikowane lub poprzedzone znakiem zmiany znaczenia, bezpieczne, to można pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry 

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*). 
        // The resulting LDAP statement will make the server return any object that 
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*). 
        ' The resulting LDAP statement will make the server return any object that 
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
