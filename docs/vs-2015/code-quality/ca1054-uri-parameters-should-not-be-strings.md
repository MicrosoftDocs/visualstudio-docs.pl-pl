---
title: 'CA1054: parametry identyfikatora URI nie powinny być ciągami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2062c7518545300074a0377b7a9cca7ddf1a8aa5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603379"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: Parametry identyfikatora URI nie powinny być ciągami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ deklaruje metodę z parametrem ciągu, którego nazwa zawiera "URI", "URI", "urn", "urn", "URL" lub "URL", a typ nie deklaruje odpowiedniego przeciążenia, które przyjmuje parametr <xref:System.Uri?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Ta reguła dzieli nazwę parametru na tokeny na podstawie Konwencji notacji CamelCase wielkości liter i sprawdza, czy każdy token jest równy "URI", "URI", "urn", "urn", "URL" lub "URL". Jeśli istnieje dopasowanie, reguła zakłada, że parametr reprezentuje jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Jeśli metoda przyjmuje ciąg reprezentujący identyfikator URI, należy dostarczyć odpowiednie Przeciążenie, które przyjmuje wystąpienie klasy <xref:System.Uri>, która udostępnia te usługi w bezpieczny i bezpieczny sposób.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień parametr na typ <xref:System.Uri>; jest to istotna zmiana. Alternatywnie Podaj Przeciążenie metody, która przyjmuje parametr <xref:System.Uri>; jest to zmiana nieprzerwana.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli parametr nie reprezentuje identyfikatora URI, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ, `ErrorProne`, który narusza tę regułę i typ `SaferWay`, który spełnia regułę.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Przekaż obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Przeciążenia identyfikatora URI w postaci ciągu wywołują przeciążenia metody System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
