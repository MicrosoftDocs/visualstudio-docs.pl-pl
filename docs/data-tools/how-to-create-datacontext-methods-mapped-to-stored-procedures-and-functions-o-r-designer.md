---
title: Mapuj metody DataContext do sprocs i Functions (Projektant O-R)
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0c1545313ba6852765bc86d57f2149b4481e5f57
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282140"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Instrukcje: tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)

Możesz dodać procedury składowane i funkcje do **projektanta O/R** jako <xref:System.Data.Linq.DataContext> metody. Wywołanie metody i przekazanie w wymaganych parametrach uruchamia procedurę składowaną lub funkcję w bazie danych i zwraca dane w zwracanym typie <xref:System.Data.Linq.DataContext> metody. Aby uzyskać szczegółowe informacje na temat <xref:System.Data.Linq.DataContext> metod, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Za pomocą procedur składowanych można także zastąpić domyślne [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowanie w czasie wykonywania, które wykonuje operacje wstawiania, aktualizacji i usuwania, gdy zmiany są zapisywane z klas jednostek do bazy danych. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Tworzenie metod DataContext

Metody można tworzyć <xref:System.Data.Linq.DataContext> , przeciągając procedury składowane lub funkcje z <strong>Eksplorator serwera lub * * Eksplorator bazy danych</strong> do **projektanta o/R**.

> [!NOTE]
> Zwracany typ wygenerowanej <xref:System.Data.Linq.DataContext> metody różni się w zależności od tego, gdzie porzucasz procedurę składowaną lub funkcję w **Projektancie O/R**. Upuszczanie elementów bezpośrednio do istniejącej klasy Entity tworzy <xref:System.Data.Linq.DataContext> metodę z typem zwracanym klasy Entity. Upuszczanie elementów na pusty obszar **projektanta o/R** tworzy <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowany typ. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu jej do okienka **metod** . Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz ją i sprawdź Właściwość **zwracanego typu** w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [How to: zmiana zwracanego typu metody DataContext (Projektant O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Aby utworzyć metody DataContext, które zwracają automatycznie generowane typy

1. W **Eksplorator serwera** lub **Eksplorator bazy danych**rozwiń węzeł **procedury składowane** w bazie danych, z którą pracujesz.

2. Znajdź żądaną procedurę przechowywaną i przeciągnij ją do pustego obszaru **projektanta o/R**.

     <xref:System.Data.Linq.DataContext>Metoda jest tworzona z automatycznie generowanym typem zwracanym i pojawia się w okienku **metody** .

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Aby utworzyć metody DataContext, które mają zwracany typ klasy jednostki

1. W **Eksplorator serwera** lub **Eksplorator bazy danych**rozwiń węzeł **procedury składowane** w bazie danych, z którą pracujesz.

2. Znajdź żądaną procedurę przechowywaną i przeciągnij ją do istniejącej klasy Entity w **Projektancie O/R**.

     <xref:System.Data.Linq.DataContext>Metoda jest tworzona z typem zwracanym wybranej klasy jednostki i pojawia się w okienku **metody** .

> [!NOTE]
> Aby uzyskać informacje na temat zmiany typu zwracanego przez istniejące <xref:System.Data.Linq.DataContext> metody, zobacz [How to: Change the return Type of DataContext, Metoda (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Przewodnik: tworzenie klas LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ w C#](/dotnet/csharp/linq/linq-in-csharp)
