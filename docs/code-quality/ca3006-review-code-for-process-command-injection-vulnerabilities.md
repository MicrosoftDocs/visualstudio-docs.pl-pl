---
title: 'CA3006: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu'
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
ms.openlocfilehash: 35e41301dcf0a1358b6d063ce557212915b5f591
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841445"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP osiągnie polecenia procesu.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufane dane wejściowe, można w trosce o atakami polegającymi na iniekcji poleceń. Ataku polegającego na iniekcji poleceń, można wykonać szkodliwe polecenia na system operacyjny, naruszenie bezpieczeństwa i integralności serwera.

Ta zasada próbuje odnaleźć danych wejściowych z żądań HTTP, osiągając polecenia procesu.

> [!NOTE]
> Ta reguła nie może śledzić dane w zestawach. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP i przekazuje je do innego zestawu, który uruchamia proces, ta zasada nie wygenerowanie ostrzeżenia.

> [!NOTE]
> Brak można skonfigurować maksymalną głębokość ta zasada będzie analizowała przepływ danych między wywołania metody. Zobacz [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) dotyczące sposobu konfigurowania limitu w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Jeśli to możliwe Unikaj uruchamianie procesów w oparciu o dane wejściowe użytkownika.
- Sprawdź dane wejściowe względem znanych bezpiecznego zestawu znaków i długość.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli znasz danych wejściowych zostało zweryfikowane lub poprzedzone znakiem zmiany znaczenia, bezpieczne jest bezpieczne pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;
using System.Diagnostics;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Process p = Process.Start(input);
    }
}
```

```vb
Imports System
Imports System.Diagnostics

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs as EventArgs)
        Dim input As String = Me.Request.Form("in")
        Dim p As Process = Process.Start(input)
    End Sub
End Class
```
