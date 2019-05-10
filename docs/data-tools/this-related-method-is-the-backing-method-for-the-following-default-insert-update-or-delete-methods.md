---
title: Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a5ae70462079589ba2b63ee50cf0b7a0570e056a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457854"
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

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)