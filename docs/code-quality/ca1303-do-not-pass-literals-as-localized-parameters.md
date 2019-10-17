---
title: 'CA1303: Nie należy przekazywać literałów jako parametrów zlokalizowanych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 443fec0c9f20148d775a734137941cd7c78da889
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444396"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Nie należy przekazywać literałów jako parametrów zlokalizowanych

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Metoda przekazuje literał ciągu jako parametr do konstruktora lub metody .NET, a ten ciąg powinien być Lokalizowalny.

To ostrzeżenie jest zgłaszane, gdy ciąg literału zostanie przesunięty jako wartość do parametru lub właściwości, co najmniej jeden z następujących przypadków ma wartość true:

- Atrybut <xref:System.ComponentModel.LocalizableAttribute> parametru lub właściwości jest ustawiony na wartość true.

- Nazwa parametru lub właściwości zawiera tekst "text", "Message" lub "Caption".

- Nazwa parametru ciągu, który jest przesyłany do konsoli. Write lub Console. WriteLine ma wartość "value" lub "format".

## <a name="rule-description"></a>Opis reguły

Literały ciągu, które są osadzone w kodzie źródłowym, są trudne do zlokalizowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zastąp literał ciągu ciągiem pobranym przez wystąpienie klasy <xref:System.Resources.ResourceManager>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli biblioteka kodu nie zostanie zlokalizowana, można bezpiecznie pominąć ostrzeżenie z tej reguły lub jeśli nie jest on widoczny dla użytkownika końcowego lub dewelopera przy użyciu biblioteki kodu.

Użytkownicy mogą wyeliminować hałas względem metod, które nie powinny być przenoszone do zlokalizowanych ciągów przez zmianę nazwy parametru lub właściwości lub poprzez oznaczenie tych elementów jako warunku.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metodę, która zgłasza wyjątek, gdy jeden z dwóch argumentów jest poza zakresem. Dla pierwszego argumentu Konstruktor wyjątku jest przenoszona jako ciąg literału, co narusza tę regułę. Dla drugiego argumentu Konstruktor prawidłowo przeszedł ciąg pobrany przez <xref:System.Resources.ResourceManager>.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index)
