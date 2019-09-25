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
ms.openlocfilehash: 6763fd9f8999bd590511026f6571db6a747c43bc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231857"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Pisownia literałów powinna być poprawna

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Ciąg literału jest przenoszona jako argument dla lokalizowalnego parametru lub do właściwości lokalizowalnej, a ciąg zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni firmy Microsoft.

## <a name="rule-description"></a>Opis reguły

Ta reguła sprawdza ciąg literału, który jest przesyłany jako wartość do parametru lub właściwości, gdy spełniony jest co najmniej jeden z następujących przypadków:

- <xref:System.ComponentModel.LocalizableAttribute> Atrybut parametru lub właściwości jest ustawiony na wartość true.

- Nazwa parametru lub właściwości zawiera tekst "text", "Message" lub "Caption".

- Nazwa zmiennej ciągu, która jest przenoszona do <xref:System.Console.Write%2A> metody lub <xref:System.Console.WriteLine> ma wartość "value" lub "format".

Ta reguła analizuje ciąg literału w słowach, tokenizowanie wyrazy złożone i sprawdza pisownię każdego wyrazu lub tokenu. Aby uzyskać informacje na temat algorytmu analizy, [zobacz CA1704: Identyfikatory powinny być poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)napisane.

## <a name="language"></a>Język

Sprawdzanie pisowni jest obecnie sprawdzane tylko w przypadku słowników kulturowych opartych na języku angielskim. Kulturę projektu można zmienić w pliku projektu, dodając element **CodeAnalysisCulture** .

Na przykład:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> W przypadku ustawienia kultury na coś innego niż kultura oparta na języku angielskim ta reguła analizy kodu jest dyskretnie wyłączona.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Popraw pisownię wyrazu lub Dodaj słowo do słownika niestandardowego. Informacje o sposobach korzystania z słowników niestandardowych można [znaleźć w temacie How to: Dostosowywanie słownika](../code-quality/how-to-customize-the-code-analysis-dictionary.md)analizy kodu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Prawidłowo napisane wyrazy zmniejszają krzywą szkoleniową wymaganą dla nowych bibliotek oprogramowania.

## <a name="related-rules"></a>Powiązane reguły

- [CA1704: Identyfikatory powinny być poprawnie napisane](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Ciągi zasobów powinny być poprawnie napisane](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)