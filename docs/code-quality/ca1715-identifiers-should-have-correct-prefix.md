---
title: 'CA1715: Identyfikatory powinny mieć poprawny prefiks'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b794eb7c7a258a843763b2c68902000031c17eb3
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873607"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Identyfikatory powinny mieć poprawny prefiks

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Przerywanie — gdy wywoływane na interfejsach.<br /><br /> Bez podziału — gdy wywoływane w parametrach typu ogólnego.|

## <a name="cause"></a>Przyczyna

Nazwa interfejsu nie rozpoczyna się od wielkie litery "I".

—lub—

Nazwa [parametr typu ogólnego](/dotnet/csharp/programming-guide/generics/generic-type-parameters) na typie lub metodzie nie zaczyna się od wielkiej litery t ".

Domyślnie ta reguła przegląda tylko interfejsy widoczne na zewnątrz, typy i metody, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Według Konwencji nazwy niektórych elementów programowania zaczynać od określonego prefiksu.

Nazwy interfejsów powinna rozpoczynać się wielką który "I" następuje innego wielką literą. Ta zasada zgłasza naruszenia nazwy interfejsu, takie jak "MyInterface" i "IsolatedInterface".

Nazwy parametrów typu ogólnego powinien zaczynać się wielką t "i opcjonalnie może następować innego wielką literą. Ta zasada zgłasza naruszenia nazwy parametru typu ogólnego, takie jak "V" i "Type".

Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="configurability"></a>Konfigurowalne

Jeśli używasz tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu), można skonfigurować, które części kodu ta reguła analizuje. Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Parametry typu pojedynczych znaków

Można skonfigurować, czy mają być wykluczone parametrów typu pojedynczych znaków od tej reguły. Na przykład, aby określić, że ta zasada *nie powinien* analizowania parametrów typu pojedynczych znaków, należy dodać jedną z następujących par klucz wartość do pliku .editorconfig w projekcie:

```
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Ta reguła jest uruchamiana nigdy nie parametru typu o nazwie `T`, na przykład `Collection<T>`.

### <a name="api-surface"></a>Powierzchni interfejsu API

Części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.ca1715.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazewnictwa).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę identyfikatora, tak, aby poprawnie jest poprzedzana.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="interface-naming-example"></a>Przykład nazewnictwa interfejsu

Poniższy fragment kodu przedstawia niepoprawnie nazwane interfejs:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

Poniższy fragment kodu usuwa wcześniejszego naruszenia praw przez dodanie przedrostka interfejsu prefiksem "I":

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Przykład nazewnictwa parametr typu

Poniższy fragment kodu przedstawia parametrem niepoprawnie nazwany typ ogólny:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

Poniższy fragment kodu poprawki wcześniejszego naruszenia praw, dodając parametr typu ogólnego przy użyciu t ":

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1722: Identyfikatory nie powinny mieć niepoprawnego prefiksu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)