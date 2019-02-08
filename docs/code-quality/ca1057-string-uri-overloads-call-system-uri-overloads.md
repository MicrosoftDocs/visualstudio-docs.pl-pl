---
title: 'CA1057: Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cd22a228f0963e2bdc87df284402d119a0353c68
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922533"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ deklaruje przeciążenia metody, które różnią się jedynie zastąpienia ciąg parametrem <xref:System.Uri?displayProperty=fullName> parametr i przeciążenia, które przyjmuje parametr typu ciąg, nie wywołuje przeciążenia przyjmującego <xref:System.Uri> parametru.

## <a name="rule-description"></a>Opis reguły
 Ponieważ przeciążenia różnią się tylko ciąg lub <xref:System.Uri> parametr ciągu zakłada się, że reprezentują jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia te usługi w bezpieczny sposób. Aby czerpać korzyści ze <xref:System.Uri> klasy, należy wywołać przeciążenie typu ciąg <xref:System.Uri> przeciążenia, przy użyciu argumentu ciągu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ponownie metody, która używa reprezentację ciągu identyfikatora URI, tak aby tworzy wystąpienie <xref:System.Uri> przy użyciu argumentu ciągu, a następnie przekazuje <xref:System.Uri> obiekt do przeciążenia, które ma <xref:System.Uri> parametru.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr typu ciąg nie reprezentuje identyfikator URI.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje przeciążenie dla typu string poprawnie zaimplementowana.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2234: Przekazuj obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Identyfikator URI zwracanych wartości nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)