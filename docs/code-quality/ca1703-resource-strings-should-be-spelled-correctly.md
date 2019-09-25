---
title: 'CA1703: Pisownia ciągów zasobów powinna być poprawna'
ms.date: 03/28/2018
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
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234323"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Pisownia ciągów zasobów powinna być poprawna

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.

## <a name="rule-description"></a>Opis reguły

Ta reguła analizuje ciąg zasobu w słowach (tokenizowanie złożone wyrazy) i sprawdza pisownię każdego wyrazu/tokenu. Aby uzyskać informacje na temat algorytmu analizy, [zobacz CA1704: Identyfikatory powinny być poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)napisane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, użyj kompletnych słów, które są poprawnie napisane lub Dodaj wyrazy do słownika niestandardowego. Aby uzyskać informacje o sposobach używania słowników niestandardowych [, zobacz CA1704: Identyfikatory powinny być poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)napisane.

## <a name="change-the-dictionary-language"></a>Zmiana języka słownika

Domyślnie używana jest wersja angielskojęzyczna (EN) modułu sprawdzania pisowni. Jeśli chcesz zmienić język sprawdzania pisowni, możesz to zrobić, dodając jeden z następujących atrybutów do pliku *AssemblyInfo.cs* lub *AssemblyInfo. vb* :

- Użyj <xref:System.Reflection.AssemblyCultureAttribute> , aby określić kulturę, jeśli zasoby znajdują się w zestawie satelickim.
- Użyj <xref:System.Resources.NeutralResourcesLanguageAttribute> , aby określić *neutralną kulturę* zestawu, jeśli zasoby znajdują się w tym samym zestawie, w którym znajduje się kod.

> [!IMPORTANT]
> W przypadku ustawienia kultury na coś innego niż kultura oparta na języku angielskim ta reguła analizy kodu jest dyskretnie wyłączona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Prawidłowo napisane wyrazy skracają czas wymagany do nauczenia się nowych bibliotek oprogramowania.

## <a name="related-rules"></a>Powiązane reguły

- [CA1701 Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Identyfikatory powinny być poprawnie napisane](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Literały powinny być poprawnie napisane](../code-quality/ca2204-literals-should-be-spelled-correctly.md)