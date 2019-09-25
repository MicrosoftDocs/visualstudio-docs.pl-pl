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
ms.openlocfilehash: e6bd77a49690979ea7ab3c4619fdd578a80bb77c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235524"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ deklaruje przeciążenia metody, które różnią się tylko zastępowaniem parametru <xref:System.Uri?displayProperty=fullName> ciągu parametrem, a Przeciążenie, które pobiera parametr String, nie wywołuje przeciążenia, które <xref:System.Uri> pobiera parametr.

## <a name="rule-description"></a>Opis reguły
Ponieważ przeciążenia różnią się tylko ciągiem lub <xref:System.Uri> parametrem, przyjmuje się, że reprezentuje on jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia te usługi w bezpieczny i bezpieczny sposób. Aby skorzystać zalety <xref:System.Uri> klasy, Przeciążenie ciągu powinno <xref:System.Uri> wywoływać przeciążenie przy użyciu argumentu ciągu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Ponownie Zaimplementuj metodę, która używa ciągu reprezentującego identyfikator URI, aby tworzył wystąpienie <xref:System.Uri> klasy za pomocą argumentu String, a następnie <xref:System.Uri> przekazuje obiekt do przeciążenia, które ma <xref:System.Uri> parametr.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli parametr ciągu nie reprezentuje identyfikatora URI, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje poprawnie zaimplementowane Przeciążenie ciągu.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA2234 Przekaż obiekty System. URI zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: Zwracane wartości identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)