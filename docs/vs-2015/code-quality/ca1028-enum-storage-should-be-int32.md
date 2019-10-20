---
title: 'CA1028: Magazyn wyliczeniowy powinien mieć wartość Int32 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc1039cb547a48c4f2dd3ea869b46d4706e9c3a2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661903"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Pamięć wyliczenia powinna być Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Podstawowy typ wyliczenia publicznego nie jest <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Domyślnie typ danych <xref:System.Int32?displayProperty=fullName> jest używany do przechowywania wartości stałej. Mimo że można zmienić ten typ podstawowy, nie jest to konieczne ani zalecane w przypadku większości scenariuszy. Należy pamiętać, że nie zostanie osiągnięty znaczący wzrost wydajności przy użyciu typu danych, który jest mniejszy niż <xref:System.Int32>. Jeśli nie można użyć domyślnego typu danych, należy użyć jednego z typów całkowitych zgodnych ze specyfikacją CLS (Common Language system), <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> lub <xref:System.Int64>, aby upewnić się, że wszystkie wartości wyliczenia mogą być reprezentowane w programowaniu zgodnym ze specyfikacją CLS Języki.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, chyba że występują problemy z rozmiarem lub zgodnością, użyj <xref:System.Int32>. W sytuacjach, w których <xref:System.Int32> nie jest wystarczająco duży, aby pomieścić wartości, użyj <xref:System.Int64>. Jeśli zgodność z poprzednimi wersjami wymaga mniejszego typu danych, należy użyć <xref:System.Byte> lub <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły tylko w przypadku, gdy wymagają to problemów ze zgodnością z poprzednimi wersjami. W aplikacjach niezgodność z tą regułą zwykle nie powoduje problemów. W bibliotekach, w których wymagane jest współdziałanie języków, niezgodność z tą regułą może mieć negatywny wpływ na użytkowników.

## <a name="example-of-a-violation"></a>Przykład naruszenia

### <a name="description"></a>Opis
 W poniższym przykładzie przedstawiono dwa wyliczenia, które nie używają zalecanego bazowego typu danych.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Przykład naprawy

### <a name="description"></a>Opis
 Poniższy przykład naprawia poprzednie naruszenie, zmieniając typ danych bazowych na <xref:System.Int32>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1008: Wyliczenia powinny zawierać wartość zero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Nie nadawaj wartościom wyliczenia nazwy „Reserved”](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Byte?displayProperty=fullName><xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
