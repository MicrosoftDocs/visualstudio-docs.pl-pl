---
title: 'CA2233: Operacje nie powinny powodować przepełnienia | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 52950f138354a72f7c0e781d761aa466760e3ca0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054797"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Operacje nie powinny powodować przepełnienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda wykonuje operację arytmetyczną i nie można zweryfikować operandów wcześniej w celu uniknięcia przepełnienia.

## <a name="rule-description"></a>Opis reguły
 Operacje arytmetyczne nie powinno być wykonywane bez uprzedniego sprawdzenia operandów, aby upewnić się, że wynik operacji nie jest spoza zakresu możliwych wartości dla typów danych związane. W zależności od kontekstu wykonywania i typy danych związane przepełnienie arytmetyczne może spowodować albo <xref:System.OverflowException?displayProperty=fullName> lub odrzucone najbardziej znaczące bity wyniku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zweryfikować operandy przed wykonaniem operacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli możliwe wartości argumentów nigdy nie spowoduje, że operacja arytmetyczna przepełnienia.

## <a name="example-of-a-violation"></a>Przykładem naruszenia

### <a name="description"></a>Opis
 W poniższym przykładzie metoda manipuluje liczba całkowita, która narusza tę regułę. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wymaga **Usuń** możliwość przepełnienia liczby całkowitej można wyłączyć tego ognia.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Komentarze
 Jeśli metoda w tym przykładzie zostanie przekazana <xref:System.Int32.MinValue?displayProperty=fullName>, operacja będzie niedopełnienie. Powoduje to najbardziej znaczącego bitu wyniku odrzucone. Poniższy kod pokazuje, jak ten problem wystąpi.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Dane wyjściowe

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Usuń z weryfikacją parametr wejściowy

### <a name="description"></a>Opis
 Poniższy przykład naprawia wcześniejszego naruszenia praw, weryfikując wartość danych wejściowych.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Napraw przy użyciu sprawdzonego bloku

### <a name="description"></a>Opis
 Poniższy przykład naprawia wcześniejszego naruszenia praw, opakowując operacji w sprawdzonego bloku. Jeśli operacja powoduje przepełnienie <xref:System.OverflowException?displayProperty=fullName> zostanie zgłoszony.

 Należy pamiętać, zaznaczone bloki nie są obsługiwane w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Włącz zaznaczony przepełnienie/niedopełnienie arytmetyczne
 Jeśli włączysz zaznaczone arytmetyczne przepełnienie/niedopełnienie w języku C# jest odpowiednikiem zawijania każda operacja liczby całkowitej w sprawdzonego bloku.

 **Aby włączyć zaznaczone arytmetyczne przepełnienie/niedopełnienie w języku C#**

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **właściwości**.

2. Wybierz **kompilacji** kartę, a następnie kliknij przycisk **zaawansowane**.

3. Wybierz **sprawdzaj przepełnienie/niedopełnienie arytmetyczne** i kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 <xref:System.OverflowException?displayProperty=fullName> [Operatory języka C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked i Unchecked](http://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
