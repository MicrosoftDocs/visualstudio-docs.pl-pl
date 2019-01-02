---
title: 'CA1703: Ciągi zasobów, które powinny być zapisane poprawnie'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0458fa33413023fe9ae2b693a9bf75ffacda706c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890592"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Ciągi zasobów, które powinny być zapisane poprawnie

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.

## <a name="rule-description"></a>Opis reguły

Ta reguła analizuje ciąg zasobu na słowa (tokenizowanie wyrazy złożone) oraz sprawdzając pisownię każdego wyrazu/tokenu. Aby uzyskać informacji na temat analizy algorytmu, zobacz [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, użyj kompletne wyrazy, które jest poprawna, lub Dodaj wyrażenie do słownika niestandardowego. Aby uzyskać informacje o sposobie używania słowników niestandardowych, zobacz [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Zmień język słownika

Domyślnie używany jest język angielski (en) wersję modułu sprawdzania pisowni. Jeśli chcesz zmienić język sprawdzania pisowni, możesz to zrobić, dodając jedną z następujących atrybutów do Twojej *AssemblyInfo.cs* lub *AssemblyInfo.vb* pliku:

- Użyj <xref:System.Reflection.AssemblyCultureAttribute> określić kulturę, jeśli Twoje zasoby znajdują się w zestawie satelickim.
- Użyj <xref:System.Resources.NeutralResourcesLanguageAttribute> do określenia *kultury neutralnej* zestawu w przypadku zasobów z tego samego zestawu, w jakim znajduje się kod.

> [!IMPORTANT]
> Jeśli ustawisz kultury na coś innego niż kulturę opartą na język angielski, ten reguł analizy kodu dyskretnie jest wyłączone.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Poprawnie właściwej słów skrócić czas, który jest wymagany, aby dowiedzieć się, nowe biblioteki oprogramowania.

## <a name="related-rules"></a>Powiązane reguły

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)