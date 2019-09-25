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
ms.openlocfilehash: c0c99d5d0adb145a061693f8a83b1f674e05eed4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237337"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie protokołu LDAP

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP docierają do instrukcji LDAP.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufanymi danymi wejściowymi należy mieć na uwadze ataki z wykorzystaniem protokołu LDAP (Lightweight Directory Access Protocol). Osoba atakująca może potencjalnie uruchamiać złośliwe instrukcje LDAP względem katalogów informacyjnych. Aplikacje korzystające z danych wejściowych użytkownika do konstruowania dynamicznych instrukcji LDAP do uzyskiwania dostępu do usług katalogowych są szczególnie podatne na ataki.

Ta reguła próbuje znaleźć dane wejściowe z żądań HTTP, które docierają do instrukcji LDAP.

> [!NOTE]
> Ta reguła nie może śledzić danych między zestawami. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP, a następnie przekazuje je do innego zestawu, który wykonuje instrukcję LDAP, ta reguła nie spowoduje wygenerowania ostrzeżenia.

> [!NOTE]
> Istnieje konfigurowalny limit, w jaki ta reguła będzie analizować przepływ danych w ramach wywołań metod. Zobacz [konfigurację analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) , aby dowiedzieć się, jak skonfigurować limit w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

W przypadku części instrukcji LDAP kontrolowanej przez użytkownika należy wziąć pod uwagę jedną z:
- Zezwalaj tylko na bezpieczną listę znaków niespecjalnych.
- Nie Zezwalaj na znaki specjalne
- Znaki specjalne ucieczki.

Aby uzyskać więcej wskazówek, zobacz [Arkusz Ściągawka zapobiegania iniekcji LDAP OWASP](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wiesz, że dane wejściowe zostały zweryfikowane lub zostały zmienione w celu zapewnienia bezpieczeństwa, możesz pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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
