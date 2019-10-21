---
title: 'CA1057: przeciążania identyfikatora URI ciągu wywołania system. URI przeciążenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603075"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Przeciążenia identyfikatora URI, który jest ciągiem, wywołują przeciążenia System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ deklaruje przeciążenia metody, które różnią się tylko zastępowaniem parametru ciągu ciągiem <xref:System.Uri?displayProperty=fullName>, a Przeciążenie, które przyjmuje parametr String, nie wywołuje przeciążenia, które przyjmuje parametr <xref:System.Uri>.

## <a name="rule-description"></a>Opis reguły
 Ponieważ przeciążenia różnią się tylko parametrem String/<xref:System.Uri>, przyjmuje się, że ciąg reprezentuje jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasy <xref:System.Uri> udostępniają te usługi w bezpieczny i bezpieczny sposób. Aby skorzystać zalety klasy <xref:System.Uri>, Przeciążenie ciągu powinno wywoływać przeciążenie <xref:System.Uri> przy użyciu argumentu ciągu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ponownie Zaimplementuj metodę, która używa ciągu reprezentującego identyfikator URI, aby tworzył wystąpienie klasy <xref:System.Uri> przy użyciu argumentu String, a następnie przekazuje obiekt <xref:System.Uri> do przeciążenia, które ma parametr <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli parametr ciągu nie reprezentuje identyfikatora URI, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje poprawnie zaimplementowane Przeciążenie ciągu.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2234: Przekaż obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
