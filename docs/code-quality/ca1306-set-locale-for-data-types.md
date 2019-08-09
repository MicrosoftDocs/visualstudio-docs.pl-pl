---
title: 'CA1306: Ustaw ustawienia regionalne dla typów danych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 893844741c848bee759f56dd027c9976a21902e8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922792"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Ustaw ustawienia regionalne dla typów danych

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Metoda lub Konstruktor utworzył jeden lub <xref:System.Data.DataTable?displayProperty=fullName> więcej lub <xref:System.Data.DataSet?displayProperty=fullName> wystąpienie i nie ustawił jawnie właściwości locale (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> lub <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Opis reguły
Ustawienia regionalne określają elementy prezentacji specyficzne dla kultury dla danych, takie jak formatowanie używane dla wartości liczbowych, symboli walut i kolejności sortowania. Podczas tworzenia <xref:System.Data.DataTable> lub <xref:System.Data.DataSet>należy jawnie ustawić ustawienia regionalne. Domyślnie ustawienia regionalne dla tych typów są obecną kulturą. W przypadku danych przechowywanych w bazie danych lub pliku, które są udostępniane globalnie, dla ustawień regionalnych powinna być zwykle ustawiana kultura niezmienna (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Gdy dane są współużytkowane przez kultury, użycie domyślnych ustawień regionalnych może spowodować nieprawidłowe wyświetlenie <xref:System.Data.DataSet> lub interpretację zawartości <xref:System.Data.DataTable> lub.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, jawnie ustaw ustawienia regionalne dla <xref:System.Data.DataTable> lub. <xref:System.Data.DataSet>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
W przypadku, gdy biblioteka lub aplikacja dla ograniczonego odbiorcy lokalnego nie jest dostępna, dane nie są udostępniane lub domyślne ustawienie zapewnia odpowiednie zachowanie we wszystkich obsługiwanych scenariuszach.

## <a name="example"></a>Przykład
Poniższy przykład tworzy dwa <xref:System.Data.DataTable> wystąpienia.

[!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>