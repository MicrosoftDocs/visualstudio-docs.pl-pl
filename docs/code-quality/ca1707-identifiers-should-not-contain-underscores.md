---
title: 'CA1707: Identyfikatory nie powinny zawierać znaków podkreślenia'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adfa0ccd63d0433d367b0e7278693608bb83d685
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234270"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identyfikatory nie powinny zawierać znaków podkreślenia

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Przerywanie — gdy są wywoływane w zestawach<br /><br /> Rozdzielenie — gdy zostanie wywołane w parametrach typu|

## <a name="cause"></a>Przyczyna

Nazwa identyfikatora zawiera znak podkreślenia (\_).

## <a name="rule-description"></a>Opis reguły

Według Konwencji nazwy identyfikatorów nie zawierają znaku podkreślenia (\_). Reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry.

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Usuń wszystkie znaki podkreślenia z nazwy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły

- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 Identyfikatory powinny różnić się więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
