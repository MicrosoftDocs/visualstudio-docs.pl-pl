---
title: 'CA2234: Przekaż obiekty System. URI zamiast ciągów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce5c076260886def089118a4d7211d75e0185c0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545213"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Przekazuj obiekty System.Uri zamiast ciągów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Wykonano wywołanie metody, która ma parametr ciągu, którego nazwa zawiera "URI", "URI", "urn", "urn", "URL" lub "URL"; a typ deklarujący metody zawiera odpowiednie Przeciążenie metody, która ma <xref:System.Uri?displayProperty=fullName> parametr.

## <a name="rule-description"></a>Opis reguły
 Nazwa parametru jest dzielona na tokeny na podstawie Konwencji wielkości liter notacji CamelCase, a następnie sprawdzana jest wartość "URI", "URI", "urn", "urn", "URL" lub "URL". Jeśli istnieje dopasowanie, przyjęto, że parametr reprezentuje identyfikator URI (Uniform Resource Identifier). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri>Klasa udostępnia te usługi w bezpieczny i bezpieczny sposób. Gdy istnieje wybór między dwoma przeciążeniami, które różnią się tylko reprezentacją identyfikatora URI, użytkownik powinien wybrać Przeciążenie przyjmujące <xref:System.Uri> argument.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj Przeciążenie przyjmujące <xref:System.Uri> argument.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli parametr ciągu nie reprezentuje identyfikatora URI, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, `ErrorProne` która narusza zasadę i metodę, `SaferWay` , która prawidłowo wywołuje <xref:System.Uri> Przeciążenie.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1057: Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
