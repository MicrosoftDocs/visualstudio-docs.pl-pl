---
title: 'CA3003: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie ścieżki pliku'
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
ms.openlocfilehash: c20d3efb9ea84a7e8bb22288303313ef44b2b795
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806566"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie ścieżki pliku

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP osiągnie ścieżki operacji na pliku.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe z żądania sieci web należy zachować ostrożność, użycia kontrolowanej przez użytkownika dane wejściowe podczas określania ścieżki do plików. Osoba atakująca może być możliwy odczyt pliku niezamierzonego skutkuje ujawnienie informacji poufnych danych. Lub osoba atakująca może zapisać do pliku niezamierzonego skutkuje nieuprawnione modyfikacje danych poufnych lub zagrożenia dla bezpieczeństwa serwera. Jest to typowa technika osoba atakująca [ścieżkę przechodzenia](https://www.owasp.org/index.php/Path_Traversal) uzyskiwania dostępu do plików poza katalogiem zamierzone.

Ta zasada próbuje odnaleźć danych wejściowych z żądań HTTP, osiągając ścieżki w operacji na pliku.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, która zapisuje do pliku, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w `.editorconfig` plików.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Jeśli to możliwe ograniczyć ścieżek plików na podstawie danych wejściowych użytkownika, do listy bezpiecznych jawnie znane.  Na przykład jeśli aplikacja wymaga tylko dostęp do "red.txt", "green.txt" lub "blue.txt", Zezwalaj tylko na tych wartości.
- Sprawdź, czy niezaufanych nazwy plików i Zweryfikuj, czy nazwa jest poprawnie sformułowany.
- Podczas określania ścieżki, należy używać nazw pełnej ścieżki.
- Należy unikać potencjalnie niebezpieczne konstrukcje, takie jak zmienne środowiskowe ścieżki.
- Tylko akceptować długie nazwy plików i sprawdzać poprawność długiej nazwy, jeśli użytkownik przesyła krótkie nazwy.
- Ograniczanie danych wprowadzonych przez użytkownika końcowego nieprawidłowych znaków.
- Odrzuć nazw, w którym została przekroczona długość MAX_PATH.
- Obsługa nazw plików dosłownie, bez interpretacji.
- Ustal, czy nazwa pliku reprezentuje pliku lub urządzenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli dane wejściowe zostały zweryfikowane, zgodnie z opisem w poprzedniej sekcji, to można pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is: 
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display 
            // The content to the webpage. 
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is: 
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display 
            ' The content to the webpage. 
        End Using
    End Sub
End Class
```
