---
title: 'CA2243: Literałów typu string atrybutów powinna przebiegać poprawnie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff2b4a569357210f4f0ae82fcb4da0e8d630ea54
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985899"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Literałów typu string atrybutów powinna przebiegać poprawnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Parametr literału ciągu atrybutu nie analizuje poprawnie adresu URL, identyfikator GUID lub wersji.

## <a name="rule-description"></a>Opis reguły
 Ponieważ atrybuty są uzyskiwane z <xref:System.Attribute?displayProperty=fullName>i atrybuty są używane w czasie kompilacji, tylko wartości stałych można przekazać do ich konstruktory. Parametry atrybutów reprezentujące musi wersji, identyfikatory GUID i adresy URL nie może być typizowana jako <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, i <xref:System.Version?displayProperty=fullName>, ponieważ te typy nie może być reprezentowana jako stałe. Zamiast tego musi być reprezentowana przez parametry.

 Ponieważ parametru zostanie podana jako ciąg znaków, jest możliwe, że w czasie kompilacji można przekazać parametr niepoprawnie sformatowany.

 Ta reguła używa heurystyki nazewnictwa w celu odnalezienia parametry, które reprezentują jednolity identyfikator zasobów (URI), globalnie unikatowy identyfikator (GUID) lub wersji i sprawdza, czy przekazana wartość jest poprawna.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień ciąg parametru na poprawnie sformułowany adres URL, identyfikator GUID lub wersji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr nie reprezentuje adres URL, identyfikator GUID lub wersji.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera kod dla AssemblyFileVersionAttribute, który narusza tę regułę.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 Reguła jest wyzwalana, wykonując następujące czynności:

-   Parametry, które zawierają "version" i nie można przeanalizować System.Version.

-   Parametry, które zawierają "guid" i nie można przeanalizować System.Guid.

-   Parametry, które zawierają "uri", "urn" lub "url" i nie można przeanalizować na System.Uri.

## <a name="see-also"></a>Zobacz też
 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
