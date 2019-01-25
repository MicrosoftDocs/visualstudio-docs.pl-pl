---
title: 'CA1815: Przesłoń metodę equals i operator równości w typach wartości | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e21585a7a56fde2fb46ea86adde92eecfd1a4565
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785108"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Przesłaniaj metodę equals i operator równości w typach wartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ publiczny wartości nie powoduje zastąpienia <xref:System.Object.Equals%2A?displayProperty=fullName>, ani nie implementuje operator równości (==). Ta reguła sprawdza wyliczenia.

## <a name="rule-description"></a>Opis reguły
 W przypadku typów wartości dziedziczona implementacja <xref:System.Object.Equals%2A> wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli oczekiwane użytkownikowi porównywania lub sortowania wystąpienia lub używać ich jako tabel haszowanych, typ wartości powinien implementować <xref:System.Object.Equals%2A>. Jeśli język programowania obsługuje przeładowania operatora, należy również podać implementacja Operatory równości i nierówności.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy udostępnić implementację klasy <xref:System.Object.Equals%2A>. Jeżeli jest to możliwe, należy zaimplementować operatora równości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli jedno wystąpienie typu wartości nie będą porównywane ze sobą.

## <a name="example-of-a-violation"></a>Przykładem naruszenia

### <a name="description"></a>Opis
 Poniższy przykład pokazuje strukturę (typ wartości), która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Przykład działania do naprawy

### <a name="description"></a>Opis
 Poniższy przykład naprawia wcześniejszego naruszenia praw przez zastąpienie <xref:System.ValueType.Equals%2A?displayProperty=fullName> i wdrażanie Operatory równości (==,! =).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2224: Przesłoń metodę equals, przeciążając operator equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Object.Equals%2A?displayProperty=fullName>
