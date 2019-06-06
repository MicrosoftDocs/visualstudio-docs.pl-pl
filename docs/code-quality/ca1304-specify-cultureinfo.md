---
title: 'CA1304: Określ argument CultureInfo'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6d4776f6bcbf89e95301bd2c7ef4f6f6b5680d9
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714362"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Określ argument CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda lub Konstruktor wywołuje członka mającego przeciążenie, które akceptuje <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> parametru, a metoda lub Konstruktor niewywołujący przeciążenia, które przyjmuje <xref:System.Globalization.CultureInfo> parametru. Ta zasada powoduje ignorowanie wywołania następujących metod:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Opis reguły

Gdy <xref:System.Globalization.CultureInfo> lub <xref:System.IFormatProvider?displayProperty=nameWithType> obiektu nie jest podany, wartość domyślna, która jest dostarczana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. Ponadto elementy członkowskie programu .NET wybierz domyślną kulturę i formatowanie na podstawie założeń, które mogą być niepoprawne w kodzie. Aby upewnić się, że kod działa zgodnie z oczekiwaniami dla scenariuszy, należy podać charakterystyczne dla kultury informacje zgodnie z następującymi wytycznymi:

- Jeśli wartość będzie wyświetlana dla użytkownika, należy użyć bieżącej kultury. Zobacz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Jeśli wartości są przechowywane i używane przez oprogramowanie, oznacza to, utrwalone w pliku lub bazy danych, użyć niezmiennej kultury. Zobacz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Jeśli miejsce docelowe wartość nie jest znany, mają odbiorcy danych lub dostawca określenie kultury.

Nawet jeśli domyślne zachowanie członka przeciążonego jest odpowiednia dla Twoich potrzeb, lepiej jest jawnie wywołać przeciążenie specyficzne dla kultury tak, aby Twój kod jest automatycznie dokumentowane i łatwiej utrzymywane w dobrym stanie.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> jest używana tylko w celu pobrania zlokalizowanych zasobów przy użyciu wystąpienia <xref:System.Resources.ResourceManager?displayProperty=nameWithType> klasy.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, użyj przeciążenia, które przyjmuje <xref:System.Globalization.CultureInfo> argumentu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy jest pewne, że domyślnej kultury jest odpowiednim wyborem oraz łatwości utrzymania kodu nie ma priorytet ważne rozwoju.

## <a name="example-showing-how-to-fix-violations"></a>Przykład pokazujący, jak naprawić naruszenia

W poniższym przykładzie `BadMethod` powoduje, że dwa naruszenie tej zasady. `GoodMethod` poprawia pierwszy naruszenia przez przekazanie Niezmienna kultura <xref:System.String.Compare%2A?displayProperty=nameWithType>i naprawia drugi naruszenia przez przekazanie bieżącej kultury, aby <xref:System.String.ToLower%2A?displayProperty=nameWithType> ponieważ `string3` jest wyświetlany użytkownikowi.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Przykład przedstawiający sformatowane dane wyjściowe

Poniższy przykład przedstawia efekt bieżącej kultury na domyślnym <xref:System.IFormatProvider> wybranego przez <xref:System.DateTime> typu.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Powiązane reguły

- [CA1305: Określ argument IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Zobacz także

- [Używanie klasy CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)