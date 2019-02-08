---
title: 'CA2204: Pisownia literałów powinna być poprawna'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82146c2ac997a0202c20e15492becb89a293f427
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949450"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Pisownia literałów powinna być poprawna

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Literał ciągu jest przekazywany jako argument parametru Lokalizowalny lub lokalizowalne właściwości, a ciąg zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft.

## <a name="rule-description"></a>Opis reguły

Ta reguła sprawdza, czy ciąg literału, który jest przekazywany jako wartość parametru lub właściwości, gdy dla jednego lub więcej z następujących przypadków ma wartość true:

- <xref:System.ComponentModel.LocalizableAttribute> Atrybut parametru lub właściwość jest ustawiona na wartość true.

- Nazwa parametru lub właściwości zawiera "Text", "Message" lub "Podpis".

- Nazwa zmiennej ciągu, który jest przekazywany do <xref:System.Console.Write%2A> lub <xref:System.Console.WriteLine> metodą jest "value" lub "format".

Ta reguła umożliwia przekształcanie ciągów literałów w wyrazy, tokenizowanie wyrazy złożone i sprawdza pisownię każdego wyrazu lub token. Aby uzyskać informacji na temat analizy algorytmu, zobacz [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Język

Moduł sprawdzania pisowni sprawdza obecnie wyłącznie w odniesieniu do słowników kulturę opartą na język angielski. Możesz zmienić kulturę projektu w pliku projektu, dodając **CodeAnalysisCulture** elementu.

Na przykład:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Jeśli ustawisz kultury na coś innego niż kulturę opartą na język angielski, ten reguł analizy kodu dyskretnie jest wyłączone.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Popraw pisownię wyrazu, lub Dodaj ten wyraz do słownika niestandardowego. Aby uzyskać informacje o sposobie używania słowników niestandardowych, zobacz [jak: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Poprawnie właściwej słów zmniejszyć nauki wymagany dla nowe biblioteki oprogramowania.

## <a name="related-rules"></a>Powiązane reguły

- [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Ciągi zasobów, które powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)