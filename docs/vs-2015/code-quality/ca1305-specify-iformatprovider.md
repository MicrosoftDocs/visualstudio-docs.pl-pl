---
title: 'CA1305: Określ IFormatProvider | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 299e8bfec526dc3a5e8dc166d9ab405d51037cbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661444"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Określ IFormatProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda lub Konstruktor wywołuje jeden lub więcej elementów członkowskich, które mają przeciążenia, które akceptują parametr <xref:System.IFormatProvider?displayProperty=fullName>, a metoda lub Konstruktor nie wywołuje przeciążenia, które przyjmuje parametr <xref:System.IFormatProvider>. Ta reguła ignoruje wywołania [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] metod, które są udokumentowane jako ignorowanie parametru <xref:System.IFormatProvider> i dodatkowo następujące metody:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Gdy nie podano obiektu <xref:System.Globalization.CultureInfo?displayProperty=fullName> lub <xref:System.IFormatProvider>, wartość domyślna, która jest dostarczana przez przeciążony element członkowski, może nie mieć żądanego efektu we wszystkich ustawieniach regionalnych. Ponadto [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] członkowie wybierają domyślną kulturę i formatowanie na podstawie założeń, które mogą nie być poprawne dla kodu. Aby upewnić się, że kod działa zgodnie z oczekiwaniami dla scenariuszy, należy podać informacje specyficzne dla kultury zgodnie z poniższymi wskazówkami:

- Jeśli wartość będzie wyświetlana użytkownikowi, Użyj bieżącej kultury. Zobacz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Jeśli wartość będzie przechowywana i używana przez oprogramowanie (utrwalone dla pliku lub bazy danych), użyj niezmiennej kultury. Zobacz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Jeśli nie znasz miejsca docelowego wartości, w polu odbiorca danych lub dostawca Określ kulturę.

  Należy pamiętać, że <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> służy tylko do pobierania zlokalizowanych zasobów przy użyciu wystąpienia klasy <xref:System.Resources.ResourceManager?displayProperty=fullName>.

  Nawet jeśli domyślne zachowanie przeciążonego elementu członkowskiego jest odpowiednie dla Twoich potrzeb, lepiej jest jawnie wywołać Przeciążenie specyficzne dla kultury, aby kod był samodzielny i łatwiejszy w obciążeniu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Użyj przeciążenia, które przyjmuje <xref:System.Globalization.CultureInfo> lub <xref:System.IFormatProvider> i określ argument zgodnie z wytycznymi wymienionymi wcześniej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Istnieje możliwość bezpiecznego pomijania ostrzeżenia z tej reguły, gdy jest to pewne, że domyślna wartość w obszarze domyślny język kultury/format jest poprawna, a łatwość utrzymania kodu nie jest ważnym priorytetem programistycznym.

## <a name="example"></a>Przykład
 W poniższym przykładzie `BadMethod` powoduje dwa naruszenia tej reguły. `GoodMethod` koryguje pierwsze naruszenie, przekazując niezmienną kulturę do <xref:System.String.Compare%2A>i koryguje drugie naruszenie, przekazując bieżącą kulturę do <xref:System.String.ToLower%2A>, ponieważ `string3` jest wyświetlana użytkownikowi.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje wpływ bieżącej kultury na domyślną <xref:System.IFormatProvider>, która jest wybierana przez typ <xref:System.DateTime>.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Powiązane reguły
 [CA1304: Określ klasę CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Zobacz też
 [NIB: Używanie klasy CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
