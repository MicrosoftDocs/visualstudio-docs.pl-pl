---
title: 'CA1008: wyliczenia powinny mieć zero wartości | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fbc7775d4ec41822b866868a6db6bceb353af989
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668928"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Wyliczenia powinny mieć wartość zero
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Rozdzielenie — gdy zostanie wyświetlony monit o dodanie wartości **Brak** do wyliczenia bez flagi. Przerywanie — gdy zostanie wyświetlony monit o zmianę nazwy lub usunięcie wartości wyliczenia.|

## <a name="cause"></a>Przyczyna
 Wyliczenie bez zastosowanego <xref:System.FlagsAttribute?displayProperty=fullName> nie definiuje elementu członkowskiego, który ma wartość zero; lub Wyliczenie, które ma zastosowany <xref:System.FlagsAttribute> definiuje element członkowski, który ma wartość zero, ale jego nazwę nie jest "none", lub Wyliczenie definiuje wiele elementów członkowskich o zerowej liczbie.

## <a name="rule-description"></a>Opis reguły
 Wartość domyślna niezainicjowanego wyliczenia, podobnie jak inne typy wartości, wynosi zero. Wyliczenie z atrybutami "nie flagi" powinno definiować element członkowski mający wartość zero, aby wartość domyślna była prawidłową wartością wyliczenia. W razie potrzeby Nadaj nazwę elementowi członkowskiemu "none". W przeciwnym razie Przypisz zero do najczęściej używanej składowej. Należy pamiętać, że domyślnie, jeśli wartość pierwszego wyliczenia elementu członkowskiego nie jest ustawiona w deklaracji, jego wartość wynosi zero.

 Jeśli Wyliczenie, które ma <xref:System.FlagsAttribute>, definiuje element członkowski o wartości zero, jego nazwa powinna być równa "none", aby wskazać, że nie zostały ustawione żadne wartości w wyliczeniu. Korzystanie z elementu członkowskiego o wartości zerowej do dowolnego innego celu jest sprzeczne z użyciem <xref:System.FlagsAttribute> w tym, że operatory i i lub bitowe są bezużyteczne dla elementu członkowskiego. Oznacza to, że tylko jeden element członkowski powinien mieć przypisaną wartość zero. Należy zauważyć, że jeśli wiele elementów członkowskich, które mają wartość zero występuje w wyliczeniu z atrybutami flagi, `Enum.ToString()` zwraca nieprawidłowe wyniki dla elementów członkowskich, które nie są równe zero.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły dla wyliczeń o atrybutach innych niż flagi −, zdefiniuj element członkowski, który ma wartość zero; to nie jest zmiana nieprzerwana. Dla flag — wyliczenia z atrybutami, które definiują element członkowski o wartości zero, Nazwij ten element członkowski "none" i Usuń wszystkie inne elementy członkowskie, które mają wartość zero; jest to istotna zmiana.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły z wyjątkiem flag — wyliczenia przypisane do atrybutów, które zostały wcześniej wysłane.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono dwa wyliczenia, które spełniają zasadę i Wyliczenie, `BadTraceOptions`, które naruszają regułę.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Nie nadawaj wartościom wyliczenia nazwy „Reserved”](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Enum?displayProperty=fullName>
