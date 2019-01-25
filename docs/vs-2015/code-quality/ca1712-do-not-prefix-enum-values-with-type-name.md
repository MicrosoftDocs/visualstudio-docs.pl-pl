---
title: 'CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 19b64c0d7c45bb2425ca3e59bd56f5c251feef50
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756026"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Wyliczenie zawiera element członkowski, którego nazwa zaczyna się od nazwy typu wyliczenia.

## <a name="rule-description"></a>Opis reguły
 Nazwy elementów członkowskich wyliczenia nie mają prefiksu z nazwą typu, ponieważ informacje o typie powinien być dostarczona przez narzędzia programistyczne.

 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to czas, który jest wymagany dla się nowa Biblioteka oprogramowania i zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, usuń prefiks nazwy typu z członka wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje niepoprawnie wyliczenia następuje poprawionej wersji.

 [!code-cpp[FxCop.Naming.EnumValues#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cpp/FxCop.Naming.EnumValues.cpp#1)]
 [!code-csharp[FxCop.Naming.EnumValues#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cs/FxCop.Naming.EnumValues.cs#1)]
 [!code-vb[FxCop.Naming.EnumValues#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/vb/FxCop.Naming.EnumValues.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1711: Identyfikatory nie powinny mieć niepoprawnego sufiksu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: Oznacz Typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Enum?displayProperty=fullName>
