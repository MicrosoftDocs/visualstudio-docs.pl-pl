---
title: 'CA1703: Pisownia ciągów zasobów powinna być poprawna'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4eea177ce2b47db0319fd9a13639e97bfbe37c0b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971615"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Pisownia ciągów zasobów powinna być poprawna

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