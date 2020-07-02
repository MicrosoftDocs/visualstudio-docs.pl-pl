---
title: Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 252303c4933501dd3a4672329d66ef4910238a08
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535255"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania

Ta powiązana Metoda to metoda tworzenia kopii zapasowej dla `Insert` następujących `Update` metod domyślnych, lub `Delete` . Jeśli zostanie usunięty, te metody również zostaną usunięte. Czy chcesz kontynuować?

Wybrana `DataContext` Metoda jest obecnie używana jako jedna z `Insert` `Update` metod, lub `Delete` dla jednej z klas obiektów w **projektancie o/R**. Usunięcie wybranej metody powoduje, że Klasa jednostki, która używa tej metody, przywraca domyślne zachowanie w czasie wykonywania w celu wykonania operacji INSERT, Update lub DELETE podczas aktualizacji.

## <a name="selected-method-options"></a>Opcje wybranej metody

- Aby usunąć wybraną metodę, powodując, że Klasa jednostki używa aktualizacji środowiska uruchomieniowego, kliknij przycisk **tak**.

   Wybrana metoda jest usuwana, a wszystkie klasy, które używają tej metody do przesłaniania zachowania aktualizacji są przywracane przy użyciu domyślnego LINQ to SQL zachowanie w czasie wykonywania.

- Aby zamknąć okno komunikatu, pozostawiając wybraną metodę bez zmian, kliknij przycisk **nie**.

   Okno komunikatu zostanie zamknięte i nie wprowadzono żadnych zmian.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)