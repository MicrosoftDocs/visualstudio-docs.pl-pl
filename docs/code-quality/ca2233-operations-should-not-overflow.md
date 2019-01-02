---
title: 'CA2233: Operacje nie powinny powodować przepełnienia'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 273fb94f4f0b66badef60178635fe3db360f73a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954581"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Operacje nie powinny powodować przepełnienia

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda wykonuje operację arytmetyczną i nie można zweryfikować operandów wcześniej w celu uniknięcia przepełnienia.

## <a name="rule-description"></a>Opis reguły

Nie należy wykonywać operacji arytmetycznych bez uprzedniego sprawdzenia operandów, aby upewnić się, że wynik operacji nie jest spoza zakresu możliwych wartości dla typów danych związane. W zależności od kontekstu wykonywania i typy danych związane przepełnienie arytmetyczne może spowodować albo <xref:System.OverflowException?displayProperty=fullName> lub odrzucone najbardziej znaczące bity wyniku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zweryfikować operandy przed wykonaniem operacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli możliwe wartości argumentów nigdy nie spowoduje, że operacja arytmetyczna przepełnienia.

## <a name="example-of-a-violation"></a>Przykładem naruszenia

W poniższym przykładzie metoda manipuluje liczba całkowita, która narusza tę regułę. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wymaga **Usuń** możliwość przepełnienia liczby całkowitej można wyłączyć tego ognia.

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

Jeśli metoda w tym przykładzie zostanie przekazana <xref:System.Int32.MinValue?displayProperty=fullName>, operacja będzie niedopełnienie. Powoduje to najbardziej znaczącego bitu wyniku odrzucone. Poniższy kod pokazuje, jak ten problem wystąpi.

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

Dane wyjściowe:

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Usuń z weryfikacją parametr wejściowy

Poniższy przykład naprawia wcześniejszego naruszenia praw, weryfikując wartość danych wejściowych.

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Napraw przy użyciu sprawdzonego bloku

Poniższy przykład naprawia wcześniejszego naruszenia praw, opakowując operacji w sprawdzonego bloku. Jeśli operacja powoduje przepełnienie <xref:System.OverflowException?displayProperty=fullName> zostanie zgłoszony.

Bloki zaznaczenia nie są obsługiwane w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Włącz zaznaczony przepełnienie/niedopełnienie arytmetyczne

Jeśli włączysz zaznaczone arytmetyczne przepełnienie/niedopełnienie w języku C# jest odpowiednikiem zawijania każda operacja liczby całkowitej w sprawdzonego bloku.

Aby włączyć funkcję kontroli arytmetyczne przepełnienie/niedopełnienie w języku C#:

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **właściwości**.

2.  Wybierz **kompilacji** kartę, a następnie kliknij przycisk **zaawansowane**.

3.  Wybierz **sprawdzaj przepełnienie/niedopełnienie arytmetyczne** i kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- <xref:System.OverflowException?displayProperty=fullName>
- [Operatory języka C#](/dotnet/csharp/language-reference/operators/index)
- [Checked i Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)