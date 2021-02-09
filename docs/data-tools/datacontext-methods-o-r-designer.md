---
title: Metody DataContext — Projektant O-R)
description: Zrozumienie metod DataContext w kontekście narzędzi LINQ to SQL Tools for Visual Studio. Te metody uruchamiają procedury składowane i funkcje w bazie danych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 64b5643704024ee689a011f5285b41be818dc5cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858972"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (Object Relational Designer)

<xref:System.Data.Linq.DataContext> Metody (w kontekście [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) to metody <xref:System.Data.Linq.DataContext> klasy, która uruchamia procedury składowane i funkcje w bazie danych.

<xref:System.Data.Linq.DataContext>Klasa jest [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasą, która działa jako kanał między bazą danych SQL Server i [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasami jednostek mapowanymi do tej bazy danych. <xref:System.Data.Linq.DataContext>Klasa zawiera informacje o parametrach połączenia oraz metody łączenia się z bazą danych i manipulowania danymi w bazie danych programu. Domyślnie <xref:System.Data.Linq.DataContext> Klasa zawiera kilka metod, które można wywołać, takich jak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Metoda, która wysyła zaktualizowane dane z [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klas do bazy danych. Możesz również utworzyć dodatkowe <xref:System.Data.Linq.DataContext> metody, które mapują na procedury składowane i funkcje. Innymi słowy, wywoływanie tych metod niestandardowych powoduje uruchomienie procedury składowanej lub funkcji w bazie danych, do której <xref:System.Data.Linq.DataContext> Metoda jest zamapowana. Nowe metody można dodać do <xref:System.Data.Linq.DataContext> klasy tak samo jak w przypadku dodawania metod w celu rozbudowania dowolnej klasy. Jednak w dyskusjach dotyczących <xref:System.Data.Linq.DataContext> metod w kontekście **projektanta o/R** są to <xref:System.Data.Linq.DataContext> metody, które mapują na procedury składowane i funkcje, które są omawiane.

## <a name="methods-pane"></a>Okienko metod

<xref:System.Data.Linq.DataContext> metody, które są mapowane na procedury składowane i funkcje, są wyświetlane w okienku **metody** **projektanta o/R**. Okienko **metody** jest okienkiem obok okienka **jednostki** (głównej powierzchni projektowej). W okienku **metody** są wyświetlane wszystkie <xref:System.Data.Linq.DataContext> metody, które zostały utworzone przy użyciu **projektanta o/R**. Domyślnie okienko **metody** jest puste; Przeciągnij procedury składowane lub funkcje z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta O/R** , aby utworzyć <xref:System.Data.Linq.DataContext> metody i wypełnić okienko **metody** . Aby uzyskać więcej informacji, zobacz [How to: Create DataContext Methods zamapowany na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otwórz i zamknij okienko metody, klikając prawym przyciskiem myszy **projektanta O/R** , a następnie klikając polecenie **Ukryj okienko metody** lub **Pokaż okienko metody** lub użyj skrótu klawiaturowego **Ctrl** + **1**.

## <a name="two-types-of-datacontext-methods"></a>Dwa typy metod DataContext

Metody DataContext to te metody, które mapują na procedury składowane i funkcje w bazie danych. Metody DataContext można tworzyć i dodawać w okienku **metody** **projektanta o/R**. Istnieją dwa odrębne typy <xref:System.Data.Linq.DataContext> metod: te, które zwracają jeden lub więcej zestawów wyników, a także te, które to nie są

- <xref:System.Data.Linq.DataContext> metody, które zwracają jeden lub więcej zestawów wyników:

   Utwórz ten rodzaj <xref:System.Data.Linq.DataContext> metody, gdy aplikacja musi uruchamiać procedury składowane i funkcje w bazie danych i zwracać wyniki. Aby uzyskać więcej informacji, zobacz [How to: Create DataContext Methods zamapowanych na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), system. Data. LINQ. ISingleResult \<T> i <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext> metody, które nie zwracają zestawów wyników: takie jak INSERT, Updates i usunięć dla określonej klasy jednostki.

   Utwórz ten rodzaj <xref:System.Data.Linq.DataContext> metody, gdy aplikacja musi uruchamiać procedury składowane zamiast korzystać z domyślnego [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowania do zapisywania zmodyfikowanych danych między klasą jednostki a bazą danych. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Zwracane typy metod DataContext

Gdy przeciągasz procedury składowane i funkcje z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta O/R**, zwracany typ wygenerowanej <xref:System.Data.Linq.DataContext> metody różni się w zależności od miejsca, w którym element zostanie porzucany. Porzucenie elementów bezpośrednio do istniejącej klasy jednostek tworzy <xref:System.Data.Linq.DataContext> metodę z typem zwracanym klasy Entity; upuszczanie elementów na pusty obszar **projektanta o/R** (w obu okienka) tworzy <xref:System.Data.Linq.DataContext> metodę, która zwraca typ wygenerowany automatycznie. Typ wygenerowany automatycznie ma nazwę zgodną z nazwą procedury składowanej lub funkcją oraz właściwościami, które mapują do pól zwracanych przez procedurę składowaną lub funkcję.

> [!NOTE]
> Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu jej do okienka metod. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz ją i sprawdź Właściwość **zwracanego typu** w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [How to: zmiana zwracanego typu metody DataContext (Projektant O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Obiekty przeciągane z bazy danych na powierzchnię projektanta O/R są nazywane automatycznie, na podstawie nazw obiektów w bazie danych. Jeśli przeciągniesz ten sam obiekt więcej niż raz, do końca nowej nazwy zostanie dodany numer odróżniający nazwy. Gdy nazwy obiektów bazy danych zawierają spacje lub znaki nieobsługiwane w Visual Basic lub C#, spacja lub nieprawidłowy znak jest zastępowany podkreśleniem.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedury składowane](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Instrukcje: tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Przewodnik: dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
