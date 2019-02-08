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
ms.openlocfilehash: 47faa5e496585940f61f94bb6dfb0b8d9d70f752
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932745"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Ustaw ustawienia regionalne dla typów danych

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda lub Konstruktor utworzony co najmniej jeden <xref:System.Data.DataTable?displayProperty=fullName> lub <xref:System.Data.DataSet?displayProperty=fullName> wystąpień i nie jawnie ustawiona właściwość locale (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> lub <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Opis reguły
 Ustawienia regionalne określą elementy prezentacji charakterystyczne dla kultury dla danych, takich jak formatowanie używane dla wartości liczbowych, symbole walut i porządek sortowania. Po utworzeniu <xref:System.Data.DataTable> lub <xref:System.Data.DataSet>, należy jawnie ustawić ustawienia regionalne. Domyślnie ustawienia regionalne dla tych typów jest bieżącej kultury. Dla danych, które są przechowywane w bazie danych lub pliku i są udostępniane globalnie, ustawienia regionalne zazwyczaj powinna być ustawiona na niezmiennej kultury (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Gdy dane są dzielone między kultur, przy użyciu domyślnych ustawień regionalnych może spowodować zawartość <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> mają być wyświetlone lub niepoprawnie interpretowane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy jawnie ustawić ustawienia regionalne <xref:System.Data.DataTable> lub <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, biblioteka lub aplikacji jest ograniczona odbiorców lokalnych, danych nie jest udostępniony lub domyślne ustawienie daje żądane zachowanie we wszystkich obsługiwanych scenariuszach.

## <a name="example"></a>Przykład
 Poniższy przykład tworzy dwie <xref:System.Data.DataTable> wystąpień.

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>