---
title: 'CA1306: Ustaw ustawienia regionalne dla typów danych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: edd1d6a7623f96f03403883ee2585d245414bb3b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539025"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Ustaw ustawienia regionalne dla typów danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda lub Konstruktor utworzył jeden lub więcej <xref:System.Data.DataTable?displayProperty=fullName> lub <xref:System.Data.DataSet?displayProperty=fullName> wystąpienie i nie ustawił jawnie właściwości locale ( <xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> lub <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName> ).

## <a name="rule-description"></a>Opis reguły
 Ustawienia regionalne określają elementy prezentacji specyficzne dla kultury dla danych, takie jak formatowanie używane dla wartości liczbowych, symboli walut i kolejności sortowania. Podczas tworzenia lub należy <xref:System.Data.DataTable> <xref:System.Data.DataSet> jawnie ustawić ustawienia regionalne. Domyślnie ustawienia regionalne dla tych typów są obecną kulturą. W przypadku danych przechowywanych w bazie danych lub pliku, które są udostępniane globalnie, dla ustawień regionalnych powinna być zwykle ustawiana kultura niezmienna ( <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> ). Gdy dane są współużytkowane przez kultury, użycie domyślnych ustawień regionalnych może spowodować nieprawidłowe wyświetlenie lub <xref:System.Data.DataTable> <xref:System.Data.DataSet> interpretację zawartości lub.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, jawnie ustaw ustawienia regionalne dla <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku, gdy biblioteka lub aplikacja dla ograniczonego odbiorcy lokalnego nie jest dostępna, dane nie są udostępniane lub domyślne ustawienie zapewnia odpowiednie zachowanie we wszystkich obsługiwanych scenariuszach.

## <a name="example"></a>Przykład
 Poniższy przykład tworzy dwa <xref:System.Data.DataTable> wystąpienia.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
