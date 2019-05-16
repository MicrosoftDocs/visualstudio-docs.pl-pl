---
title: 'CA1305: Określ argument IFormatProvider | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 93bf7f17f77008ce8e9898c1871926edf2e8439f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694770"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Określ argument IFormatProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda lub Konstruktor wywołują jednego lub więcej członków, którzy mają przeciążenia akceptujące <xref:System.IFormatProvider?displayProperty=fullName> parametru, a metoda lub Konstruktor niewywołujący przeciążenia, które przyjmuje <xref:System.IFormatProvider> parametru. Ta zasada powoduje ignorowanie wywołania [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] metody, które są udokumentowane jako ignorowanie <xref:System.IFormatProvider> parametru, a ponadto następujących metod:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Gdy <xref:System.Globalization.CultureInfo?displayProperty=fullName> lub <xref:System.IFormatProvider> obiektu nie jest podany, wartość domyślna, która jest dostarczana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. Ponadto [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] członków wybierz domyślną kulturę i formatowanie na podstawie założeń, które mogą być niepoprawne w kodzie. Aby upewnić się, że kod działa zgodnie z oczekiwaniami dla scenariuszy, należy podać informacje specyficzne dla kultury, zgodnie z następującymi wytycznymi:

- Jeśli wartość będzie wyświetlana dla użytkownika, należy użyć bieżącej kultury. Zobacz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Jeśli wartości są przechowywane i używane przez oprogramowanie (utrwalone w pliku lub bazy danych), należy użyć niezmiennej kultury. Zobacz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Jeśli miejsce docelowe wartość nie jest znany, mają odbiorcy danych lub dostawca określenie kultury.

  Należy pamiętać, że <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> służy tylko do pobrania zlokalizowanych zasobów przy użyciu wystąpienia <xref:System.Resources.ResourceManager?displayProperty=fullName> klasy.

  Nawet jeśli domyślne zachowanie członka przeciążonego jest odpowiednia dla Twoich potrzeb, lepiej jest jawnie wywołać przeciążenie specyficzne dla kultury tak, aby Twój kod jest automatycznie dokumentowane i łatwiej utrzymywane w dobrym stanie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, użyj przeciążenia, które przyjmuje <xref:System.Globalization.CultureInfo> lub <xref:System.IFormatProvider> i określić argument, zgodnie z wytycznymi, które zostały wymienione wcześniej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy jest pewne, czy domyślny dostawca kultury/format jest odpowiednim wyborem i gdzie łatwości utrzymania kodu nie jest priorytetem ważne rozwoju.

## <a name="example"></a>Przykład
 W poniższym przykładzie `BadMethod` powoduje, że dwa naruszenie tej zasady. `GoodMethod` poprawia pierwszy naruszenia przez przekazanie Niezmienna kultura <xref:System.String.Compare%2A>i naprawia drugi naruszenia przez przekazanie bieżącej kultury, aby <xref:System.String.ToLower%2A> ponieważ `string3` jest wyświetlany użytkownikowi.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia efekt bieżącej kultury na domyślnym <xref:System.IFormatProvider> wybranego przez <xref:System.DateTime> typu.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **6/4/1900 12:15:12 PM**
**06-04-1900 12:15:12**
## <a name="related-rules"></a>Powiązane reguły
 [CA1304: Określ klasę CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Zobacz też
 [NIB: Używanie klasy CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
