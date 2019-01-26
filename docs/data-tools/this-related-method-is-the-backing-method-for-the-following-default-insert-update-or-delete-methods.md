---
title: Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4b478f041dcd94cff58f9bff8121e8d6e3b8acd3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069346"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania

Ta powiązana metoda to metoda zapasowa następujące domyślne `Insert`, `Update`, lub `Delete` metody. Jeśli zostanie usunięta, te metody także zostaną usunięte. Czy chcesz kontynuować?

Wybrane `DataContext` metoda jest obecnie używany jako jeden z `Insert`, `Update`, lub `Delete` metody dla jednej z klas jednostek na **O/R Designer**. Usunięcie przyczyny wybranej metody Klasa jednostki, która została przy użyciu tej metody, aby powrócić do domyślnego zachowania czasu wykonywania do operacji wstawiania, aktualizowania lub usuwania podczas aktualizacji.

## <a name="selected-method-options"></a>Opcje wybrane metody

- Aby usunąć wybranej metody, powodując Klasa jednostki do korzystania z aktualizacji środowiska uruchomieniowego, kliknij przycisk **tak**.

   Wybranej metody zostanie usunięty, a wszystkie klasy, które umożliwiający zastępowanie zachowania aktualizacji tej metody są przywracane przy użyciu domyślnego LINQ do zachowania w czasie wykonywania SQL.

- Aby zamknąć okno komunikatu, pozostawiając wybranej metody bez zmian, kliknij przycisk **nie**.

   Zamyka okno komunikatu, i są wprowadzane żadne zmiany.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)