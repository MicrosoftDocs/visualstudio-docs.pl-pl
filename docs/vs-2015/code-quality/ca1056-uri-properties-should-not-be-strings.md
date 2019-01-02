---
title: 'CA1056: Właściwości identyfikatora URI nie powinny być ciągami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cbae3f526acbc948d11a7510a70c03be76ff20b8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916447"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: Właściwości identyfikatora URI nie powinny być ciągami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ deklaruje właściwość ciągu, którego nazwa zawiera "uri", "Uri", "urn", "Urn", "url" lub "Url".

## <a name="rule-description"></a>Opis reguły
 Ta reguła dzieli nazwy właściwości na tokeny oparte na Konwencji obudowy Pascal i sprawdza, czy każdy token jest równa "uri", "Uri", "urn", "Urn", "url" lub "Url". Jeśli istnieje dopasowanie, reguła zakłada, że właściwość reprezentuje identyfikator uniform resource identifier (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri?displayProperty=fullName> Klasa udostępnia te usługi w bezpieczny sposób.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić właściwość <xref:System.Uri> typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli właściwość reprezentuje identyfikator URI.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typem `ErrorProne`, który narusza tę regułę, a typem `SaferWay`, odpowiadającej reguły.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Identyfikator URI zwracanych wartości nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Przekazuj obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Przeciążenia identyfikatora URI ciągu wywołują przeciążenia System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
