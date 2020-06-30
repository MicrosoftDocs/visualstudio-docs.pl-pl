---
title: 'CA2217: nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b584e355f5b64984f57dd17606dfb0a2f781c62d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547670"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Widoczne na zewnątrz Wyliczenie jest oznaczone za pomocą <xref:System.FlagsAttribute> i ma co najmniej jedną wartość, która nie ma uprawnień dwóch lub kombinacji innych zdefiniowanych wartości w wyliczeniu.

## <a name="rule-description"></a>Opis reguły
 Wyliczenie powinno być <xref:System.FlagsAttribute> dostępne tylko wtedy, gdy każda wartość zdefiniowana w wyliczeniu jest potęgą dwóch lub kombinacji zdefiniowanych wartości.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Usuń <xref:System.FlagsAttribute> z wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje Wyliczenie, kolor, który zawiera wartość 3, która nie jest potęgą dwóch ani nie ma kombinacji wartości zdefiniowanych przez siebie. Wyliczenie koloru nie powinno być oznaczone <xref:System.FlagsAttribute> .

 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cpp/FxCop.Usage.EnumNoFlags.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cs/FxCop.Usage.EnumNoFlags.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/vb/FxCop.Usage.EnumNoFlags.vb#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono Wyliczenie, dni, które spełniają wymagania oznaczone przez element System. FlagsAttribute.

 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cpp/FxCop.Usage.EnumNoFlags2.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cs/FxCop.Usage.EnumNoFlags2.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/vb/FxCop.Usage.EnumNoFlags2.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.FlagsAttribute?displayProperty=fullName>
