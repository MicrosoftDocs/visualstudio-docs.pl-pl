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
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252574"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identyfikatory nie powinny zawierać znaków podkreślenia

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft.Naming|
|Zmiana podziału|Przerywanie — gdy są wywoływane w zestawach<br /><br /> Rozdzielenie — gdy zostanie wywołane w parametrach typu|

## <a name="cause"></a>Przyczyna

Nazwa identyfikatora zawiera znak podkreślenia (\_).

## <a name="rule-description"></a>Opis reguły

Według Konwencji nazwy identyfikatorów nie zawierają znaku podkreślenia (\_). Reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry.

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Usuń wszystkie znaki podkreślenia z nazwy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla kodu produkcyjnego. Można jednak bezpiecznie pominąć to ostrzeżenie dla kodu testu. Możesz pominąć ostrzeżenia z tej reguły, ustawiając jej [ważność](use-roslyn-analyzers.md#rule-severity) na **none**. 

## <a name="related-rules"></a>Powiązane reguły

- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter @ no__t-0
- [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter @ no__t-0
