---
title: 'CA1309: Użyj porządkowego StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34054f6f444e503077c1e81da9f08ae2832d635a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661429"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Użyj porządkowego StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Operacja porównywania ciągów, która nie jest językiem, nie ustawia parametru <xref:System.StringComparison> na wartość **porządkową** lub **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Opis reguły
 Wiele operacji na ciągach, co jest najważniejszymi metodami <xref:System.String.Compare%2A?displayProperty=fullName> i <xref:System.String.Equals%2A?displayProperty=fullName>, udostępnia teraz Przeciążenie, które akceptuje <xref:System.StringComparison?displayProperty=fullName> wartość wyliczenia jako parametr.

 Po określeniu wartości **StringComparison. porządkowych** lub **StringComparison. OrdinalIgnoreCase**, Porównywanie ciągów będzie nielingwistyczne. Oznacza to, że funkcje, które są specyficzne dla języka naturalnego są ignorowane w przypadku podejmowania decyzji dotyczących porównania. Oznacza to, że decyzje są oparte na prostych porównaniach bajtów i ignorowanie wielkości liter lub tabel równoważności, które są sparametryzowane przez kulturę. W związku z tym poprzez jawne ustawienie parametru na **StringComparison. numer porządkowy** lub **StringComparison. OrdinalIgnoreCase**, kod często uzyskuje szybkość, zwiększa poprawność i jest bardziej niezawodny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić metodę porównywania ciągów na Przeciążenie, które akceptuje Wyliczenie <xref:System.StringComparison?displayProperty=fullName> jako parametr, i określić wartość **porządkową** lub **OrdinalIgnoreCase**. Na przykład zmień `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy biblioteka lub aplikacja jest przeznaczona dla ograniczonej liczby odbiorców lokalnych lub gdy należy używać semantyki bieżącej kultury.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia globalizacji](../code-quality/globalization-warnings.md) [CA1307: Określ StringComparison](../code-quality/ca1307-specify-stringcomparison.md)
