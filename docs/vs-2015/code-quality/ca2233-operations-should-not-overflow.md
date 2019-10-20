---
title: 'CA2233: operacje nie powinny przepełniać | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 70a0bab8cfb3bf14a763f759e0e44a754ad878d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662781"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Operacje nie powinny prowadzić do przepełnienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Metoda wykonuje operację arytmetyczną i nie sprawdza wcześniej operandów, aby zapobiec przepełnieniu.

## <a name="rule-description"></a>Opis reguły
 Nie należy wykonywać operacji arytmetycznych bez uprzedniego sprawdzenia operandów, aby upewnić się, że wynik operacji nie należy do zakresu możliwych wartości dla typów danych. W zależności od kontekstu wykonywania i typów danych, przepełnienie arytmetyczne może skutkować <xref:System.OverflowException?displayProperty=fullName> lub najbardziej znaczących bitów wyniku odrzucone.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, przed wykonaniem operacji Sprawdź poprawność operandów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli możliwe wartości operandów nigdy nie spowodują przepełnienia operacji arytmetycznej, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example-of-a-violation"></a>Przykład naruszenia

### <a name="description"></a>Opis
 Metoda w poniższym przykładzie operuje liczbą całkowitą, która narusza tę regułę. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wymaga wyłączenia opcji przepełnienia **liczby całkowitej** , aby można było ją uruchomić.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Komentarze
 Jeśli metoda w tym przykładzie jest przenoszona <xref:System.Int32.MinValue?displayProperty=fullName>, operacja spowodowałaby niedopełnienie. Powoduje to najbardziej znaczący bit wyniku, który ma zostać odrzucony. Poniższy kod pokazuje, jak to się dzieje.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 VB

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

## <a name="fix-with-input-parameter-validation"></a>Napraw przy użyciu walidacji parametru wejściowego

### <a name="description"></a>Opis
 Poniższy przykład naprawia poprzednie naruszenie, sprawdzając wartość danych wejściowych.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Popraw z zaznaczonym blokiem

### <a name="description"></a>Opis
 Poniższy przykład naprawia poprzednie naruszenie przez zapakowanie operacji w zaznaczonym bloku. Jeśli operacja powoduje przepełnienie, zostanie zgłoszony <xref:System.OverflowException?displayProperty=fullName>.

 Należy zauważyć, że zaznaczone bloki nie są obsługiwane w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Włącz sprawdzone przepełnienie arytmetyczne/niedomiar
 W przypadku włączenia sprawdzania przepełnienia arytmetycznego/ C#przeciążenia w programie jest on równoznaczny z zamiarem zawijania każdej operacji całkowitej w zaznaczonym bloku.

 **Aby włączyć sprawdzanie przepełnienia arytmetycznego/przeciążenia wC#**

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

2. Wybierz kartę **kompilacja** , a następnie kliknij pozycję **Zaawansowane**.

3. Wybierz pozycję **Sprawdź, aby uzyskać arytmetyczne przepełnienie/niedomiar** i kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [zaznaczone i](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e) niezaznaczone [ C# operatory](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) <xref:System.OverflowException?displayProperty=fullName>
