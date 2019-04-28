---
title: 'CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fdae06137586f11de1a30a73894c46c7fb18fa6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546287"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Ciąg zasobu zawiera wyraz złożony, który nie ma mieć prawidłową wielkość liter.

## <a name="rule-description"></a>Opis reguły

Każdego wyrazu w ciągu zasobu jest podzielony na tokeny, które są oparte na wielkość liter w wyrazie. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły. Przykłady wyrazy złożone, powodujących naruszenie to "CheckSum" i "MultiPart", które powinny być pisane w formie "Checksum" i "Multipart", odpowiednio. Ze względu na poprzednie powszechnie kilkoma wyjątkami są wbudowane w zasady i są oznaczane kilka pojedyncze wyrazy, takie jak "Toolbar" i "Filename", które powinny być pisane w formie dwóch unikatowych słów. W tym przykładzie zostanie oznaczony "ToolBar" i "FileName".

Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień litery słowo, dzięki czemu jest poprawna.

## <a name="change-the-dictionary-language"></a>Zmień język słownika

Domyślnie używany jest język angielski (en) wersję modułu sprawdzania pisowni. Jeśli chcesz zmienić język sprawdzania pisowni, możesz to zrobić, dodając jedną z następujących atrybutów do Twojej *AssemblyInfo.cs* lub *AssemblyInfo.vb* pliku:

- Użyj <xref:System.Reflection.AssemblyCultureAttribute> określić kulturę, jeśli Twoje zasoby znajdują się w zestawie satelickim.
- Użyj <xref:System.Resources.NeutralResourcesLanguageAttribute> do określenia *kultury neutralnej* zestawu w przypadku zasobów z tego samego zestawu, w jakim znajduje się kod.

> [!IMPORTANT]
> Jeśli ustawisz kultury na coś innego niż kulturę opartą na język angielski, ten reguł analizy kodu dyskretnie jest wyłączone.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli obie części wyraz złożony są rozpoznawane przez słownik sprawdzania pisowni, a celem jest użycie dwóch słów.

Możesz również dodać wyrazy złożone do słownika niestandardowego sprawdzania pisowni. Wyrazy do słownika nie powodują naruszenia. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Zobacz także

- [Konwencje dotyczące wielkości liter](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Wskazówki dotyczące nazewnictwa](/dotnet/standard/design-guidelines/naming-guidelines)