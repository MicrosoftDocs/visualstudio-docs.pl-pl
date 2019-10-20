---
title: Mapuj metody DataContext do sprocs i Functions (Projektant O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4fa392467024a38dc447e6a5077f855d3464103b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648370"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Instrukcje: Tworzenie metod DataContext mapowanych na procedury składowane i funkcje (Projektant O/R)

Możesz dodać procedury składowane i funkcje do **projektanta O/R** jako metody <xref:System.Data.Linq.DataContext>. Wywołanie metody i przekazanie w wymaganych parametrach powoduje uruchomienie procedury składowanej lub funkcji w bazie danych i zwrócenie danych w zwracanym typie metody <xref:System.Data.Linq.DataContext>. Aby uzyskać szczegółowe informacje na temat metod <xref:System.Data.Linq.DataContext>, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Można również użyć procedur składowanych, aby zastąpić domyślny [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowanie w czasie wykonywania, które wykonuje operacje wstawiania, aktualizacji i usuwania, gdy zmiany są zapisywane z klas jednostek do bazy danych. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Tworzenie metod DataContext

Metody <xref:System.Data.Linq.DataContext> można tworzyć, przeciągając procedury składowane lub funkcje z <strong>Eksplorator serwera lub * * Eksplorator bazy danych</strong> do **projektanta o/R**.

> [!NOTE]
> Zwracany typ wygenerowanej metody <xref:System.Data.Linq.DataContext> różni się w zależności od tego, gdzie porzucasz procedurę składowaną lub funkcję w **Projektancie O/R**. Upuszczanie elementów bezpośrednio do istniejącej klasy Entity tworzy metodę <xref:System.Data.Linq.DataContext> z typem zwracanym klasy Entity. Upuszczanie elementów na pusty obszar **projektanta o/R** tworzy metodę <xref:System.Data.Linq.DataContext>, która zwraca typ wygenerowany automatycznie. Zwracany typ metody <xref:System.Data.Linq.DataContext> można zmienić po dodaniu jej do okienka **metod** . Aby sprawdzić lub zmienić zwracany typ metody <xref:System.Data.Linq.DataContext>, zaznacz ją i sprawdź Właściwość **zwracanego typu** w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [How to: zmiana zwracanego typu metody DataContext (Projektant O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Aby utworzyć metody DataContext, które zwracają automatycznie generowane typy

1. W **Eksplorator serwera** lub **Eksplorator bazy danych**rozwiń węzeł **procedury składowane** w bazie danych, z którą pracujesz.

2. Znajdź żądaną procedurę przechowywaną i przeciągnij ją do pustego obszaru **projektanta o/R**.

     Metoda <xref:System.Data.Linq.DataContext> jest tworzona z automatycznie generowanym typem zwracanym i pojawia się w okienku **metody** .

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Aby utworzyć metody DataContext, które mają zwracany typ klasy jednostki

1. W **Eksplorator serwera** lub **Eksplorator bazy danych**rozwiń węzeł **procedury składowane** w bazie danych, z którą pracujesz.

2. Znajdź żądaną procedurę przechowywaną i przeciągnij ją do istniejącej klasy Entity w **Projektancie O/R**.

     Metoda <xref:System.Data.Linq.DataContext> jest tworzona z typem zwracanym wybranej klasy jednostki i pojawia się w okienku **metody** .

> [!NOTE]
> Aby uzyskać informacje na temat zmieniania typu zwracanego istniejących metod <xref:System.Data.Linq.DataContext>, zobacz [How to: Change the return Type of DataContext, Metoda (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Przewodnik: tworzenie klas LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ w C#](/dotnet/csharp/linq/linq-in-csharp)
