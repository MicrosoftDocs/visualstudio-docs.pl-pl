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
ms.openlocfilehash: 986607d7f42f49c99396bbb021c48bad549930c9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237283"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Potencjalnie niezaufane dane wejściowe żądania HTTP docierają do procesu.

## <a name="rule-description"></a>Opis reguły

Podczas pracy z niezaufanymi danymi wejściowymi należy zastanowić się nad atakami polegającymi na iniekcji poleceń. Atak polegający na iniekcji poleceń może wykonywać złośliwe polecenia w podstawowym systemie operacyjnym, narażając zabezpieczenia i integralność serwera.

Ta reguła próbuje znaleźć dane wejściowe z żądań HTTP, które docierają do polecenia procesu.

> [!NOTE]
> Ta reguła nie może śledzić danych między zestawami. Na przykład jeśli jeden zestaw odczytuje dane wejściowe żądania HTTP, a następnie przekazuje je do innego zestawu, który uruchamia proces, ta reguła nie spowoduje wygenerowania ostrzeżenia.

> [!NOTE]
> Istnieje konfigurowalny limit, w jaki ta reguła będzie analizować przepływ danych w ramach wywołań metod. Zobacz [konfigurację analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) , aby dowiedzieć się, jak skonfigurować limit w pliku EditorConfig.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Jeśli to możliwe, unikaj uruchamiania procesów na podstawie danych wejściowych użytkownika.
- Sprawdzaj poprawność danych wejściowych dla znanego, bezpiecznego zestawu znaków i długości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wiesz, że dane wejściowe zostały zweryfikowane lub zostały zmienione w celu zapewnienia bezpieczeństwa, możesz bezpiecznie pominąć to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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
