---
title: 'CA2243: Analiza literałów ciągów atrybutów powinna przebiegać poprawnie'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c0f078c21de023b1f5cfacde0cf122c179adb2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919901"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Analiza literałów ciągów atrybutów powinna przebiegać poprawnie

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
Parametr literału ciągu atrybutu nie jest analizowany poprawnie dla adresu URL, identyfikatora GUID lub wersji.

## <a name="rule-description"></a>Opis reguły
Ponieważ atrybuty są wyprowadzane <xref:System.Attribute?displayProperty=fullName>z, a atrybuty są używane w czasie kompilacji, tylko stałe wartości mogą być przesyłane do ich konstruktorów. Parametry atrybutu, które muszą reprezentować adresy URL, identyfikatory GUID i wersje, <xref:System.Uri?displayProperty=fullName>nie <xref:System.Guid?displayProperty=fullName>mogą być <xref:System.Version?displayProperty=fullName>wpisane jako, i, ponieważ te typy nie mogą być reprezentowane jako stałe. Zamiast tego muszą być reprezentowane przez ciągi.

Ponieważ parametr jest typu String, istnieje możliwość, że nieprawidłowo sformatowany parametr może zostać przesłany w czasie kompilacji.

Ta reguła używa algorytmu heurystycznego nazewnictwa, aby znaleźć parametry, które reprezentują jednolity identyfikator zasobów (URI), unikatowy identyfikator globalny (GUID) lub wersję, i sprawdza, czy wartość przeniesiona jest poprawna.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Zmień ciąg parametru na poprawnie sformułowany adres URL, identyfikator GUID lub wersję.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli parametr nie reprezentuje adresu URL, identyfikatora GUID lub wersji, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje kod dla AssemblyFileVersionAttribute, który narusza tę regułę.

[!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

Reguła jest wyzwalana przez następujące parametry:

- Parametry, które zawierają element "Version" i nie mogą zostać przeanalizowane do System. Version.

- Parametry, które zawierają "GUID" i nie można przeanalizować do System. GUID.

- Parametry, które zawierają "URI", "urn" lub "URL" i nie mogą zostać przeanalizowane do System. URI.

## <a name="see-also"></a>Zobacz także

- [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)