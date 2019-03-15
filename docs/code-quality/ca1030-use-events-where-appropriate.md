---
title: 'CA1030: Używaj zdarzeń, o ile to możliwe'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1054fa7b884c23edb76248cba17bab41cc64246f
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867435"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Używaj zdarzeń, o ile to możliwe

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Nazwa metody rozpoczyna się od jednego z następujących czynności:

- AddOn
- RemoveOn
- Ogień
- Zgłoś

Domyślnie ta reguła przegląda tylko widocznych zewnętrznie metod, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Zdarzenia wykonaj wzorzec projektowy obserwatora lub publikowania i subskrybowania; są one używane podczas zmiany stanu, w jeden obiekt musi zostać przekazany innych obiektów. Jeśli metoda jest wywoływana w odpowiedzi na jasno określoną zmianę stanu, metoda powinna być wywoływany przez program obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę.

Typowe przykłady zdarzeń znajdują się w aplikacji interfejsu użytkownika, gdy akcja użytkownika, takie jak kliknięcie przycisku powoduje, że segment kodu do wykonania. Model zdarzenia .NET Framework nie jest ograniczona do interfejsów użytkownika; powinno być używane wszędzie tam, gdzie muszą komunikować się, że stan zmieni się na co najmniej jeden obiekt.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Jeśli metoda jest wywoływana, gdy zmieni się stan obiektu, należy rozważyć zmianę projektu do korzystania z modelu zdarzeń platformy .NET.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomijaj ostrzeżeń dla tej reguły, jeśli metoda nie działa z modelu zdarzeń platformy .NET.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.ca1030.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).