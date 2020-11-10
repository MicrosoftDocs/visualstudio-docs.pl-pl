---
title: Zmień zwracany typ metody DataContext
description: Dowiedz się, jak zmienić zwracany typ metody DataContext podczas upuszczania procedury składowanej lub funkcji w Object Relational Designer (Projektant O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 20ff0e4764acf4f2f0f8dea77ed815a9aa430abe
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435055"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Instrukcje: zmienianie zwracanego typu metody DataContext (O/R Designer)
Zwracany typ <xref:System.Data.Linq.DataContext> metody (utworzony w oparciu o procedurę składowaną lub funkcję) różni się w zależności od tego, gdzie porzucasz procedurę składowaną lub funkcję w **Projektancie O/R**. W przypadku porzucenia elementu bezpośrednio do istniejącej klasy jednostki <xref:System.Data.Linq.DataContext> zostanie utworzona Metoda, która ma zwracany typ klasy jednostki (Jeśli schemat danych zwróconych przez procedurę składowaną lub funkcję dopasowuje kształt klasy jednostki). Jeśli powrócisz element do pustego obszaru **projektanta o/R** , <xref:System.Data.Linq.DataContext> zostanie utworzona Metoda zwracająca automatycznie wygenerowany typ. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu jej do okienka metod. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz ją i kliknij właściwość **Typ zwracany** w oknie **Właściwości** .

> [!NOTE]
> Nie można przywrócić <xref:System.Data.Linq.DataContext> metod, które mają ustawiony typ zwracany na klasę jednostki, aby zwracał typ wygenerowany automatycznie przy użyciu okna **Właściwości** . Aby przywrócić <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowany typ, należy ponownie przeciągnąć oryginalny obiekt bazy danych do **projektanta O/R** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Aby zmienić zwracany typ metody DataContext z automatycznie generowanego typu do klasy Entity

1. Wybierz <xref:System.Data.Linq.DataContext> metodę w okienku metody.

2. W oknie **Właściwości** wybierz pozycję **Typ zwracany** , a następnie wybierz dostępną klasę jednostki na liście **Typ zwracany** . Jeśli żądana Klasa jednostki nie znajduje się na liście, Dodaj ją do lub Utwórz w **Projektancie O/R** , aby dodać ją do listy.

3. Zapisz plik *. dbml* .

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Aby zmienić zwracany typ metody DataContext z klasy Entity z powrotem na typ wygenerowany automatycznie

1. Wybierz <xref:System.Data.Linq.DataContext> metodę w okienku **metody** i usuń ją.

2. Przeciągnij obiekt bazy danych z **Eksplorator serwera** lub **Eksplorator bazy danych** do pustego obszaru **projektanta o/R**.

3. Zapisz plik *. dbml* .

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
