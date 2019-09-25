---
title: 'CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5480d3dde926dfe31b018a5cd0b1ea6a5813063b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234334"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Przerywanie — gdy są uruchamiane w zestawach.<br /><br /> Rozdzielenie — gdy jest uruchamiany w parametrach typu.|

## <a name="cause"></a>Przyczyna

Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jeden z nich wydaje się wyrazem złożonym, w którym wielkość liter nie jest poprawna.

## <a name="rule-description"></a>Opis reguły

Nazwa identyfikatora jest dzielona na wyrazy, które są oparte na wielkości liter. Każda ciągła kombinacja dwóch wyrazów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeśli zostanie rozpoznany, identyfikator powoduje naruszenie reguły. Przykładami wyrazów złożonych, które powodują naruszenie, są "CheckSum" i "wieloczęściowa", które powinny być odpowiednio określone jako "Checksum" i "wieloczęściowa". Ze względu na poprzednie typowe użycie, kilka wyjątków jest wbudowanych w regułę, a kilka pojedynczych wyrazów jest oflagowanych, takich jak "Toolbar" i "filename", które powinny być rozróżniane jako dwa oddzielne słowa (w tym przypadku "ToolBar" i "FileName").

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę tak, aby była uwzględniana wielkość liter.

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

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli obie części wyrazu złożonego są rozpoznawane przez słownik pisowni, można bezpiecznie pominąć ostrzeżenie z tej reguły, a zamiarem jest użycie dwóch wyrazów.

## <a name="related-rules"></a>Powiązane reguły

- [CA1701 Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 Identyfikatory powinny różnić się więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące nazewnictwa](/dotnet/standard/design-guidelines/naming-guidelines)
- [Konwencje dotyczące wielkości liter](/dotnet/standard/design-guidelines/capitalization-conventions)