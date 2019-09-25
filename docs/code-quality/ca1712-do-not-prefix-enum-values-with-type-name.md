---
title: 'CA1712: Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0b5966c9685bc4bbc5ba997f8acf47abbbfca1a2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234113"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Wyliczenie zawiera element członkowski, którego nazwa rozpoczyna się od nazwy typu wyliczenia.

## <a name="rule-description"></a>Opis reguły
Nazwy elementów członkowskich wyliczenia nie są poprzedzone nazwą typu, ponieważ oczekuje się, że informacje o typie są udostępniane przez narzędzia deweloperskie.

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Pozwala to skrócić czas wymagany przez program, aby poznać nową bibliotekę oprogramowania i zwiększyć zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Usuń prefiks nazwy typu z elementu członkowskiego wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje nieprawidłowo nazwane Wyliczenie, a po nim poprawioną wersję.

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1711 Identyfikatory nie powinny mieć niepoprawnego sufiksu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027 Oznacz typy wyliczeniowe atrybutem FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217 Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Enum?displayProperty=fullName>