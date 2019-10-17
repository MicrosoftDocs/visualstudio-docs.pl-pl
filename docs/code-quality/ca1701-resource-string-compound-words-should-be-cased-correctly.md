---
title: 'CA1701: Wyrazy złożone ciągu zasobu należy zapisywać z uwzględnieniem wielkości liter'
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
ms.openlocfilehash: c5d7aa3c29ca8ba82f6c50b070c5210cf10d1884
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443928"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Wyrazy złożone ciągu zasobu należy zapisywać z uwzględnieniem wielkości liter

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Ciąg zasobu zawiera wyraz złożony, który nie jest wyświetlany w przypadku poprawnego wielkości liter.

## <a name="rule-description"></a>Opis reguły

Każdy wyraz w ciągu zasobu jest podzielony na tokeny, które są oparte na wielkości liter. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły. Przykładami wyrazów złożonych, które powodują naruszenie, są "CheckSum" i "wieloczęściowa", które powinny być odpowiednio określone jako "Checksum" i "wieloczęściowa". Ze względu na poprzednie typowe użycie, kilka wyjątków jest wbudowanych w regułę, a kilka pojedynczych wyrazów jest oflagowanych, takich jak "Toolbar" i "filename", które powinny być uwzględniane w przypadku dwóch odrębnych wyrazów. W tym przykładzie "ToolBar" i "FileName" byłyby oflagowane.

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień słowo tak, aby była uwzględniana wielkość liter.

## <a name="change-the-dictionary-language"></a>Zmiana języka słownika

Domyślnie używana jest wersja angielskojęzyczna (EN) modułu sprawdzania pisowni. Jeśli chcesz zmienić język sprawdzania pisowni, możesz to zrobić, dodając jeden z następujących atrybutów do pliku *AssemblyInfo.cs* lub *AssemblyInfo. vb* :

- Użyj <xref:System.Reflection.AssemblyCultureAttribute>, aby określić kulturę, jeśli zasoby znajdują się w zestawie satelickim.
- Użyj <xref:System.Resources.NeutralResourcesLanguageAttribute>, aby określić *neutralną kulturę* zestawu, jeśli zasoby znajdują się w tym samym zestawie, w którym znajduje się kod.

> [!IMPORTANT]
> W przypadku ustawienia kultury na coś innego niż kultura oparta na języku angielskim ta reguła analizy kodu jest dyskretnie wyłączona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli obie części wyrazu złożonego są rozpoznawane przez słownik pisowni, można bezpiecznie pominąć ostrzeżenie z tej reguły, a zamiarem jest użycie dwóch wyrazów.

Możesz również dodać wyrazy złożone do słownika niestandardowego dla narzędzia sprawdzania pisowni. Słowa w słowniku niestandardowym nie powodują naruszeń. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Zobacz także

- [Konwencje dotyczące wielkości liter](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Wskazówki dotyczące nazewnictwa](/dotnet/standard/design-guidelines/naming-guidelines)
