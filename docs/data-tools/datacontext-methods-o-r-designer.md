---
title: Metody DataContext (Projektant O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 83ca0059e576683571435764914bf0087eded2fa
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951166"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (O/R Designer)

<xref:System.Data.Linq.DataContext> metody (w kontekście [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) to metody <xref:System.Data.Linq.DataContext> klasę, która uruchamianie procedur przechowywanych i funkcji w bazie danych.

<xref:System.Data.Linq.DataContext> Klasa jest [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasę, która działa jako kanał między bazy danych programu SQL Server i [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klas jednostek mapowany do tej bazy danych. <xref:System.Data.Linq.DataContext> Klasa zawiera informacje o parametrach połączenia i metody nawiązywania połączenia z bazą danych i manipulowania danymi w bazie danych. Domyślnie <xref:System.Data.Linq.DataContext> klasa zawiera kilka metod, które można wywoływać, takich jak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodę, która wysyła zaktualizowane dane z [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy do bazy danych. Można również utworzyć dodatkowe <xref:System.Data.Linq.DataContext> metod, które mapują do procedur przechowywanych i funkcji. Innymi słowy, wywoływanie tych metod niestandardowego uruchamia procedurę składowaną lub funkcję w bazie danych do której <xref:System.Data.Linq.DataContext> metody jest zamapowany. Możesz dodać nowe metody <xref:System.Data.Linq.DataContext> klasy tak, jak należy dodać metody umożliwiające rozszerzenie dowolnej klasy. Jednak w dyskusje na temat <xref:System.Data.Linq.DataContext> metod w kontekście **O/R Designer**, jest <xref:System.Data.Linq.DataContext> metod, które mapują do procedur przechowywanych i funkcji, które są przedmiotem.

## <a name="methods-pane"></a>Okienko metod

<xref:System.Data.Linq.DataContext> metody, które mapują do procedur przechowywanych i funkcji są wyświetlane w **metody** okienku **O/R Designer**. **Metody** okienko to okienko wzdłuż boku **jednostek** okienko (główna powierzchnia projektowa). **Metody** okienko zawiera wszystkie <xref:System.Data.Linq.DataContext> metod, które zostały utworzone przy użyciu **O/R Designer**. Domyślnie **metody** okienko jest puste; przeciągnij przechowywane procedury lub funkcji z **Eksploratora serwera** lub **Eksplorator bazy danych** na **Relational Designer**  utworzyć <xref:System.Data.Linq.DataContext> metod i wypełnić **metody** okienka. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otwórz i Zamknij okienko metod, klikając prawym przyciskiem myszy **O/R Designer** , a następnie klikając polecenie **Ukryj okienko metod** lub **Pokaż okienko metod**, lub użyj skrótu klawiaturowego  **CTRL**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Dwa typy metod DataContext

Metody DataContext są tych metod, które mapują do procedur przechowywanych i funkcji w bazie danych. Można utworzyć i dodać metodę DataContext na **metody** okienku **O/R Designer**. Istnieją dwa odrębne rodzaje <xref:System.Data.Linq.DataContext> metod; te, które zwracają jeden lub więcej zestawów wyników i te, które nie obsługują:

- <xref:System.Data.Linq.DataContext> metody, które zwracają jeden lub więcej zestawów wyników:

   Utworzyć ten rodzaju <xref:System.Data.Linq.DataContext> metody, gdy tylko wymaganych przez aplikację do uruchamiania procedur składowanych i funkcji w bazie danych i zwracają wyniki. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, a <xref:System.Data.Linq.IMultipleResults>.

- <xref:System.Data.Linq.DataContext> metody, które nie zwracają zestaw wyników: takich jak wstawia, aktualizacji i usuwania dla klasy określonej jednostki.

   Utworzyć ten rodzaju <xref:System.Data.Linq.DataContext> metody, gdy aplikacja ma do uruchamiania procedur składowanych, zamiast przy użyciu domyślnego [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowanie zapisywanie zmodyfikowanych danych między klasami jednostki oraz bazy danych. Aby uzyskać więcej informacji, zobacz [jak: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Zwracane typy metod DataContext

Podczas przeciągania procedur przechowywanych i funkcji z **Eksploratora serwera** lub **Eksplorator bazy danych** na **O/R Designer**, zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda zależy od tego, gdzie można upuścić elementu. Upuszczenie elementów bezpośrednio na istniejącej klasy jednostki tworzy <xref:System.Data.Linq.DataContext> metody z typem zwracanym klasy jednostki; upuszczanie elementów na pustym obszarem **O/R Designer** (w obu okienku) tworzy <xref:System.Data.Linq.DataContext> — metoda który zwraca typ wygenerowany automatycznie. Automatycznie wygenerowany typ zawiera nazwę, która pasuje do procedury składowanej lub nazwą funkcji i właściwości, które są mapowane na pola zwrócone przez procedurę składowaną lub funkcję.

> [!NOTE]
> Możesz zmienić typ zwracany <xref:System.Data.Linq.DataContext> metoda po dodaniu do okienka metod. Aby sprawdzić lub zmienić typ zwracany <xref:System.Data.Linq.DataContext> metody, zaznacz ją i sprawdź **typie zwracanym** właściwość **właściwości** okna. Aby uzyskać więcej informacji, zobacz [jak: Zmień zwracany typ metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Obiekty, które przeciągniesz z bazy danych na powierzchnię projektanta O/R są nazywane automatycznie na podstawie nazwy obiektów w bazie danych. Przeciągnięcie tego samego obiektu w więcej niż jeden raz, jest dodawany numer na końcu nową nazwę, która odróżnia nazwy. Gdy nazwy obiektów bazy danych zawiera spacje lub znaki nieobsługiwane w języku Visual Basic lub C#, miejsca lub nieprawidłowy znak jest zastępowany znaku podkreślenia.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedury składowane](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Instrukcje: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Przewodnik: Dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Przewodnik: Tworzenie zapytań LINQ do klas SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)