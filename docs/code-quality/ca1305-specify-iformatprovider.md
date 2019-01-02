---
title: 'CA1305: Określ argument IFormatProvider'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: fea236a51b8bde5171c91ad1935d4168dfabd94a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954240"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Określ argument IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda lub Konstruktor wywołują jednego lub więcej członków, którzy mają przeciążenia akceptujące <xref:System.IFormatProvider?displayProperty=fullName> parametru, a metoda lub Konstruktor niewywołujący przeciążenia, które przyjmuje <xref:System.IFormatProvider> parametru.

Ta zasada powoduje ignorowanie wywołania do metod .NET Framework, które są udokumentowane jako ignorowanie <xref:System.IFormatProvider> parametru. Reguła ignoruje także następujących metod:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Opis reguły

Gdy <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> lub <xref:System.IFormatProvider> obiektu nie jest podany, wartość domyślna, która jest dostarczana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. Ponadto elementy członkowskie programu .NET Framework wybierz domyślną kulturę i formatowanie na podstawie założeń, które mogą być niepoprawne w kodzie. Aby upewnić się, że kod działa zgodnie z oczekiwaniami dla scenariuszy, należy podać informacje specyficzne dla kultury, zgodnie z następującymi wytycznymi:

- Jeśli wartość będzie wyświetlana dla użytkownika, należy użyć bieżącej kultury. Zobacz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Jeśli wartości są przechowywane i używane przez oprogramowanie (utrwalone w pliku lub bazy danych), należy użyć niezmiennej kultury. Zobacz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Jeśli miejsce docelowe wartość nie jest znany, mają odbiorcy danych lub dostawca określenie kultury.

Nawet jeśli domyślne zachowanie członka przeciążonego jest odpowiednia dla Twoich potrzeb, lepiej jest jawnie wywołać przeciążenie specyficzne dla kultury tak, aby Twój kod jest automatycznie dokumentowane i łatwiej utrzymywane w dobrym stanie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, użyj przeciążenia, które przyjmuje <xref:System.IFormatProvider> argumentu. Możesz też korzystać z [C# ciągiem interpolowanym](/dotnet/csharp/tutorials/string-interpolation) i przekazać ją do <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy jest pewne, że domyślny format jest odpowiednim wyborem oraz łatwości utrzymania kodu nie ma priorytet ważne rozwoju.

## <a name="example"></a>Przykład

W poniższym kodzie `example1` ciągu narusza regułę CA1305. `example2` Ciąg spełnia reguł CA1305 przez przekazanie <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, który implementuje <xref:System.IFormatProvider>, <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. `example3` Ciąg spełnia reguł CA1305, przekazując ciąg interpolowany <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>Powiązane reguły

- [CA1304: Określ klasę CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Zobacz także

- [Używanie klasy CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)