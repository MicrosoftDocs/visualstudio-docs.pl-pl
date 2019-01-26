---
title: 'CA1030: Używaj zdarzeń, o ile to możliwe'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 89ee195da621ea9d7342302efadf582e21f7e619
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956730"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Używaj zdarzeń, o ile to możliwe

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Nazwy metody publiczne, protected lub private rozpoczyna się od jednego z następujących czynności:

- AddOn

- RemoveOn

- Ogień

- Zgłoś

## <a name="rule-description"></a>Opis reguły
 Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Zdarzenia wykonaj wzorzec projektowy obserwatora lub publikowania i subskrybowania; są one używane podczas zmiany stanu, w jeden obiekt musi zostać przekazany innych obiektów. Jeśli metoda jest wywoływana w odpowiedzi na jasno określoną zmianę stanu, metoda powinna być wywoływany przez program obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę.

 Typowe przykłady zdarzeń znajdują się w aplikacji interfejsu użytkownika, gdy akcja użytkownika, takie jak kliknięcie przycisku powoduje, że segment kodu do wykonania. Model zdarzenia .NET Framework nie jest ograniczona do interfejsów użytkownika; powinno być używane wszędzie tam, gdzie muszą komunikować się, że stan zmieni się na co najmniej jeden obiekt.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli metoda jest wywoływana, gdy zmieni się stan obiektu, należy rozważyć zmianę projektu do korzystania z modelu zdarzenia .NET Framework.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli metoda nie działa w programie .NET Framework model zdarzeń.