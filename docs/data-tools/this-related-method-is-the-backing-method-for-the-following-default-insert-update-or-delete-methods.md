---
title: Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8a7a422cff33fd361b784fd9cae6d5053fbe84fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639666"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania

Powiązana Metoda to metoda tworzenia kopii zapasowych dla następujących domyślnych `Insert`, `Update` lub `Delete` metod. Jeśli zostanie usunięty, te metody również zostaną usunięte. Czy chcesz kontynuować?

Wybrana metoda `DataContext` jest obecnie używana jako jedna z metod `Insert`, `Update` lub `Delete` dla jednej z klas obiektów w **projektancie o/R**. Usunięcie wybranej metody powoduje, że Klasa jednostki, która używa tej metody, przywraca domyślne zachowanie w czasie wykonywania w celu wykonania operacji INSERT, Update lub DELETE podczas aktualizacji.

## <a name="selected-method-options"></a>Opcje wybranej metody

- Aby usunąć wybraną metodę, powodując, że Klasa jednostki używa aktualizacji środowiska uruchomieniowego, kliknij przycisk **tak**.

   Wybrana metoda jest usuwana, a wszystkie klasy, które używają tej metody do przesłaniania zachowania aktualizacji są przywracane przy użyciu domyślnego LINQ to SQL zachowanie w czasie wykonywania.

- Aby zamknąć okno komunikatu, pozostawiając wybraną metodę bez zmian, kliknij przycisk **nie**.

   Okno komunikatu zostanie zamknięte i nie wprowadzono żadnych zmian.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)