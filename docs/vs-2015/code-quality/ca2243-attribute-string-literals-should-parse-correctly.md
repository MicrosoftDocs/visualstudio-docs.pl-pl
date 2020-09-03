---
title: 'CA2243: literały ciągu atrybutów powinny być analizowane poprawnie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09e932651576f9b6d595657ad024b8f2697ad016
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535749"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Analiza literałów ciągów atrybutów powinna przebiegać poprawnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Parametr literału ciągu atrybutu nie jest analizowany poprawnie dla adresu URL, identyfikatora GUID lub wersji.

## <a name="rule-description"></a>Opis reguły
 Ponieważ atrybuty są wyprowadzane z <xref:System.Attribute?displayProperty=fullName> , a atrybuty są używane w czasie kompilacji, tylko stałe wartości mogą być przesyłane do ich konstruktorów. Parametry atrybutu, które muszą reprezentować adresy URL, identyfikatory GUID i wersje, nie mogą być wpisane jako <xref:System.Uri?displayProperty=fullName> , <xref:System.Guid?displayProperty=fullName> i <xref:System.Version?displayProperty=fullName> , ponieważ te typy nie mogą być reprezentowane jako stałe. Zamiast tego muszą być reprezentowane przez ciągi.

 Ponieważ parametr jest typu String, istnieje możliwość, że nieprawidłowo sformatowany parametr może zostać przesłany w czasie kompilacji.

 Ta reguła używa algorytmu heurystycznego nazewnictwa w celu znalezienia parametrów reprezentujących jednolity identyfikator zasobów (URI), unikatowy identyfikator globalny (GUID) lub wersję i sprawdza, czy wartość przeniesiona jest poprawna.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień ciąg parametru na poprawnie sformułowany adres URL, identyfikator GUID lub wersję.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli parametr nie reprezentuje adresu URL, identyfikatora GUID lub wersji, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje kod dla AssemblyFileVersionAttribute, który narusza tę regułę.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 Reguła jest wyzwalana przez następujące elementy:

- Parametry, które zawierają element "Version" i nie mogą zostać przeanalizowane do System. Version.

- Parametry, które zawierają "GUID" i nie można przeanalizować do System. GUID.

- Parametry, które zawierają "URI", "urn" lub "URL" i nie mogą zostać przeanalizowane do System. URI.

## <a name="see-also"></a>Zobacz też
 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
