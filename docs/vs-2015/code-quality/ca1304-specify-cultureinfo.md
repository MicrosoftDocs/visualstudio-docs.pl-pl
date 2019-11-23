---
title: 'CA1304: Określ CultureInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 202f3759026bbedd5e99e94bba76e956b83357b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661467"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Określ CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda lub Konstruktor wywołuje element członkowski mający Przeciążenie, które akceptuje parametr <xref:System.Globalization.CultureInfo?displayProperty=fullName>, a metoda lub Konstruktor nie wywołuje przeciążenia, które przyjmuje parametr <xref:System.Globalization.CultureInfo>. Ta reguła ignoruje wywołania następujących metod:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Gdy nie podano obiektu <xref:System.Globalization.CultureInfo> lub <xref:System.IFormatProvider?displayProperty=fullName>, wartość domyślna, która jest dostarczana przez przeciążony element członkowski, może nie mieć żądanego efektu we wszystkich ustawieniach regionalnych. Ponadto [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] członkowie wybierają domyślną kulturę i formatowanie na podstawie założeń, które mogą nie być poprawne dla kodu. Aby upewnić się, że kod działa zgodnie z oczekiwaniami dla scenariuszy, należy podać informacje specyficzne dla kultury zgodnie z poniższymi wskazówkami:

- Jeśli wartość będzie wyświetlana użytkownikowi, Użyj bieżącej kultury. Zobacz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Jeśli wartość będzie przechowywana i dostępna przez oprogramowanie, czyli utrwalone dla pliku lub bazy danych, użyj niezmiennej kultury. Zobacz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Jeśli nie znasz miejsca docelowego wartości, w polu odbiorca danych lub dostawca Określ kulturę.

  Należy pamiętać, że <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> służy tylko do pobierania zlokalizowanych zasobów przy użyciu wystąpienia klasy <xref:System.Resources.ResourceManager?displayProperty=fullName>.

  Nawet jeśli domyślne zachowanie przeciążonego elementu członkowskiego jest odpowiednie dla Twoich potrzeb, lepiej jest jawnie wywołać Przeciążenie specyficzne dla kultury, aby kod był samodzielny i łatwiejszy w obciążeniu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Użyj przeciążenia, które przyjmuje <xref:System.Globalization.CultureInfo> lub <xref:System.IFormatProvider> i określ argument zgodnie z wytycznymi wymienionymi wcześniej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Istnieje możliwość bezpiecznego pomijania ostrzeżenia z tej reguły, gdy jest to pewne, że domyślna wartość dla wybranego dostawcy kultury/formatu jest poprawna, a łatwość utrzymania kodu nie jest ważnym priorytetem programistycznym.

## <a name="example"></a>Przykład
 W poniższym przykładzie `BadMethod` powoduje dwa naruszenia tej reguły. `GoodMethod` koryguje pierwsze naruszenie, przekazując niezmienną kulturę do System. String. Compare i koryguje drugie naruszenie, przekazując bieżącą kulturę do <xref:System.String.ToLower%2A> ponieważ `string3` jest wyświetlana użytkownikowi.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje wpływ bieżącej kultury na domyślną <xref:System.IFormatProvider>, która jest wybierana przez typ <xref:System.DateTime>.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Powiązane reguły
 [CA1305: Określ interfejs IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Zobacz też
 [NIB: Używanie klasy CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
