---
title: 'CA1304: Określ CultureInfo'
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
ms.openlocfilehash: 50f4726b21b51b963074ee9ae1c161872f6a5e5a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444436"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Określ CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Metoda lub Konstruktor wywołuje element członkowski z przeciążeniem akceptującym parametr <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>, a metoda lub Konstruktor nie wywołuje przeciążenia, które przyjmuje parametr <xref:System.Globalization.CultureInfo>. Ta reguła ignoruje wywołania następujących metod:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Opis reguły

Gdy nie podano obiektu <xref:System.Globalization.CultureInfo> lub <xref:System.IFormatProvider?displayProperty=nameWithType>, wartość domyślna, która jest dostarczana przez przeciążony element członkowski, może nie mieć żądanego efektu we wszystkich ustawieniach regionalnych. Ponadto członkowie platformy .NET wybierają domyślną kulturę i formatowanie na podstawie założeń, które mogą nie być poprawne dla kodu. Aby upewnić się, że kod działa zgodnie z oczekiwaniami dla scenariuszy, należy podać informacje specyficzne dla kultury zgodnie z poniższymi wskazówkami:

- Jeśli wartość będzie wyświetlana użytkownikowi, Użyj bieżącej kultury. Zobacz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Jeśli wartość będzie przechowywana i dostępna przez oprogramowanie, czyli utrwalone dla pliku lub bazy danych, użyj niezmiennej kultury. Zobacz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Jeśli nie znasz miejsca docelowego wartości, w polu odbiorca danych lub dostawca Określ kulturę.

Nawet jeśli domyślne zachowanie przeciążonego elementu członkowskiego jest odpowiednie dla Twoich potrzeb, lepiej jest jawnie wywołać Przeciążenie specyficzne dla kultury, aby kod był samodzielny i łatwiejszy w obciążeniu.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> służy tylko do pobierania zlokalizowanych zasobów przy użyciu wystąpienia klasy <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Użyj przeciążenia, które przyjmuje <xref:System.Globalization.CultureInfo> argumentu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy jest to pewne, że domyślna kultura jest poprawna, i gdzie łatwość utrzymania kodu nie jest ważnym priorytetem programistycznym.

## <a name="example-showing-how-to-fix-violations"></a>Przykład pokazujący, jak naprawić naruszenia

W poniższym przykładzie `BadMethod` powoduje dwa naruszenia tej reguły. `GoodMethod` koryguje pierwsze naruszenie, przekazując niezmienną kulturę do <xref:System.String.Compare%2A?displayProperty=nameWithType> i koryguje drugie naruszenie, przekazując bieżącą kulturę do <xref:System.String.ToLower%2A?displayProperty=nameWithType>, ponieważ do użytkownika jest wyświetlany `string3`.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Przykład pokazujący sformatowane dane wyjściowe

Poniższy przykład pokazuje wpływ bieżącej kultury na domyślną <xref:System.IFormatProvider>, która jest wybierana przez typ <xref:System.DateTime>.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Powiązane reguły

- [CA1305: Określ interfejs IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Zobacz także

- [Korzystanie z klasy CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)
