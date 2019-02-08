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
ms.openlocfilehash: f78ea4f44c48d2740df58def03a6335bce6637a2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942768"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Istotne, kiedy jest uruchamiany na zestawach.<br /><br /> Bez podziału — gdy wywoływane w parametrach typu.|

## <a name="cause"></a>Przyczyna

Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jeden z nich wydaje się wyrazem złożonym, w którym wielkość liter nie jest poprawna.

## <a name="rule-description"></a>Opis reguły

Nazwa identyfikatora jest dzielony na wyrazy, które są oparte na wielkość liter w wyrazie. Kombinacjami word dwóch sąsiadujących jest sprawdzana przez bibliotekę sprawdzania pisowni Microsoft. Jeśli został rozpoznany identyfikator powoduje naruszenie reguły. Przykłady wyrazy złożone, powodujących naruszenie to "CheckSum" i "MultiPart", które powinny być pisane w formie "Checksum" i "Multipart", odpowiednio. Ze względu na poprzednie powszechnie kilkoma wyjątkami są wbudowane w zasady i są oznaczane kilka pojedyncze wyrazy, takie jak "Toolbar" i "Filename", które powinny mieć prawidłową wielkość jako dwa różne wyrazy (w tym przypadku "ToolBar" i "FileName").

Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę, dzięki czemu jest poprawna.

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

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli obie części wyraz złożony są rozpoznawane przez słownik sprawdzania pisowni, a celem jest użycie dwóch słów.

## <a name="related-rules"></a>Powiązane reguły

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące nazewnictwa](/dotnet/standard/design-guidelines/naming-guidelines)
- [Konwencje dotyczące wielkości liter](/dotnet/standard/design-guidelines/capitalization-conventions)