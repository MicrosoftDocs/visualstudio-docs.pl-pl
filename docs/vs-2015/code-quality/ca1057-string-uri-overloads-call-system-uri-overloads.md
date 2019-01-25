---
title: 'CA1057: Przeciążenia identyfikatora URI ciągu wywołują przeciążenia System.Uri | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4cf50ca225544b06409415320c73e7824a10843a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778276"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ deklaruje przeciążenia metody, które różnią się jedynie zastąpienia ciąg parametrem <xref:System.Uri?displayProperty=fullName> parametr i przeciążenia, które przyjmuje parametr typu ciąg, nie wywołuje przeciążenia przyjmującego <xref:System.Uri> parametru.

## <a name="rule-description"></a>Opis reguły
 Ponieważ przeciążenia różnią się tylko ciąg /<xref:System.Uri> parametr ciągu zakłada się, że reprezentują jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia te usługi w bezpieczny sposób. Aby czerpać korzyści ze <xref:System.Uri> klasy, należy wywołać przeciążenie typu ciąg <xref:System.Uri> przeciążenia, przy użyciu argumentu ciągu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ponownej implementacji metody, która używa reprezentację ciągu identyfikatora URI, tak aby tworzy wystąpienie <xref:System.Uri> przy użyciu argumentu ciągu, a następnie przekazuje <xref:System.Uri> obiekt do przeciążenia, które ma <xref:System.Uri> parametru.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr typu ciąg nie reprezentuje identyfikator URI.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje przeciążenie dla typu string poprawnie zaimplementowana.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2234: Przekazuj obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Identyfikator URI zwracanych wartości nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
