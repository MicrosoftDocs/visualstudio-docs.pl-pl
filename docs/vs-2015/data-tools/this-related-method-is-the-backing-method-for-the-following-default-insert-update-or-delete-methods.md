---
title: Ta powiązana Metoda to metoda tworzenia kopii zapasowej dla następujących domyślnych metod INSERT, Update lub DELETE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84d27dc6f5081a36a237748c091429cfdabbe841
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667178"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta powiązana Metoda to metoda tworzenia kopii zapasowej dla następujących domyślnych metod INSERT, Update lub DELETE. Jeśli zostanie usunięty, te metody również zostaną usunięte. Czy chcesz kontynuować?

 Wybrana metoda `DataContext` jest obecnie używana jako jedna z metod INSERT, Update lub DELETE dla jednej z klas obiektów w Projektancie O/R. Usunięcie wybranej metody spowoduje, że Klasa jednostki, która używa tej metody, przywraca domyślne zachowanie w czasie wykonywania dla operacji INSERT, Update lub DELETE podczas aktualizacji.

### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Aby usunąć wybraną metodę, powodując, że Klasa jednostki używa aktualizacji środowiska uruchomieniowego

- Kliknij przycisk **Tak**.

     Wybrana metoda jest usuwana, a wszystkie klasy, które używają tej metody do przesłaniania zachowania aktualizacji, są przywracane przy użyciu domyślnego zachowania środowiska uruchomieniowego LINQ to SQL.

### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Aby zamknąć okno komunikatu, pozostawiając wybraną metodę bez zmian

- Kliknij przycisk **nie**.

     Okno komunikatu zostanie zamknięte i nie wprowadzono żadnych zmian.

## <a name="see-also"></a>Zobacz też
 [Metody DataContext (program o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [instrukcje: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (Projektant O/r)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
