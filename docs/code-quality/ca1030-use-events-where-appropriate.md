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
ms.openlocfilehash: 28d71fbfc10532f7c9420ea7e847ef4c29b88854
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236079"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Używaj zdarzeń, o ile to możliwe

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Nazwa metody rozpoczyna się od jednego z następujących:

- Dodatki
- RemoveOn
- Zapala
- nosić

Domyślnie ta reguła przegląda tylko zewnętrznie widoczne metody, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Zdarzenia obserwują Wzorzec projektowy obserwatora lub publikowania/subskrybowania. są one używane, gdy zmiana stanu w jednym obiekcie musi być przekazywana do innych obiektów. Jeśli metoda zostanie wywołana w odpowiedzi na jasno zdefiniowaną zmianę stanu, metoda powinna być wywoływana przez procedurę obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę.

Niektóre typowe przykłady zdarzeń można znaleźć w aplikacjach interfejsu użytkownika, w których akcja użytkownika, taka jak kliknięcie przycisku powoduje, że segment kodu ma zostać wykonany. Model zdarzeń .NET nie jest ograniczony do interfejsów użytkownika. Należy go używać wszędzie tam, gdzie trzeba przekazywać zmiany stanu do jednego lub większej liczby obiektów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Jeśli metoda jest wywoływana, gdy zmienia się stan obiektu, należy rozważyć zmianę projektu w celu użycia modelu zdarzeń .NET.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomiń ostrzeżenie z tej reguły, jeśli metoda nie działa z modelem zdarzeń platformy .NET.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).
