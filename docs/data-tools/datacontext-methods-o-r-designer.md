---
title: Metody DataContext — Projektant O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b8b9d322ea9c805b7fc1ce55dbf93b72b29958af
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586708"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (Object Relational Designer)

Metody <xref:System.Data.Linq.DataContext> (w kontekście [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) to metody klasy <xref:System.Data.Linq.DataContext>, która uruchamia procedury składowane i funkcje w bazie danych.

Klasa <xref:System.Data.Linq.DataContext> jest klasą [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], która działa jako kanał między bazą danych SQL Server i [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy jednostek mapowanych do tej bazy danych. Klasa <xref:System.Data.Linq.DataContext> zawiera informacje o parametrach połączenia oraz metody łączenia się z bazą danych i manipulowania danymi w bazie danych programu. Domyślnie Klasa <xref:System.Data.Linq.DataContext> zawiera kilka metod, które można wywołać, takich jak Metoda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, która wysyła zaktualizowane dane z klas [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] do bazy danych. Możesz również utworzyć dodatkowe metody <xref:System.Data.Linq.DataContext>, które mapują na procedury składowane i funkcje. Innymi słowy, wywoływanie tych metod niestandardowych powoduje uruchomienie procedury składowanej lub funkcji w bazie danych, do której zamapowana jest metoda <xref:System.Data.Linq.DataContext>. Nowe metody można dodać do klasy <xref:System.Data.Linq.DataContext> tak samo jak w przypadku dodawania metod w celu poszerzenia dowolnej klasy. Jednak w dyskusjach dotyczących <xref:System.Data.Linq.DataContext> metod w kontekście **projektanta o/R**są to metody <xref:System.Data.Linq.DataContext>, które są mapowane na procedury składowane i funkcje, które są omawiane.

## <a name="methods-pane"></a>Okienko metod

Metody <xref:System.Data.Linq.DataContext>, które są mapowane na procedury składowane i funkcje, są wyświetlane w okienku **metody** **projektanta o/R**. Okienko **metody** jest okienkiem obok okienka **jednostki** (głównej powierzchni projektowej). W okienku **metody** znajduje się lista wszystkich <xref:System.Data.Linq.DataContext> metod utworzonych przy użyciu **projektanta o/R**. Domyślnie okienko **metody** jest puste; Przeciągnij procedury składowane lub funkcje z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta O/R** , aby utworzyć metody <xref:System.Data.Linq.DataContext> i wypełnić okienko **metody** . Aby uzyskać więcej informacji, zobacz [How to: Create DataContext Methods zamapowany na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otwórz i zamknij okienko metody, klikając prawym przyciskiem myszy **projektanta O/R** , a następnie klikając polecenie **Ukryj okienko metody** lub **Pokaż okienko metody**lub użyj skrótu klawiaturowego **Ctrl**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Dwa typy metod DataContext

Metody DataContext to te metody, które mapują na procedury składowane i funkcje w bazie danych. Metody DataContext można tworzyć i dodawać w okienku **metody** **projektanta o/R**. Istnieją dwa różne typy metod <xref:System.Data.Linq.DataContext>; te, które zwracają jeden lub więcej zestawów wyników, i te, które nie:

- Metody <xref:System.Data.Linq.DataContext>, które zwracają jeden lub więcej zestawów wyników:

   Utwórz ten rodzaj metody <xref:System.Data.Linq.DataContext>, gdy aplikacja musi uruchamiać procedury składowane i funkcje w bazie danych i zwracać wyniki. Aby uzyskać więcej informacji, zobacz [How to: Create DataContext Methods zamapowanych na procedury składowane i funkcje (Projektant O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), system. Data. LINQ. ISingleResult\<t > i <xref:System.Data.Linq.IMultipleResults>.

- <xref:System.Data.Linq.DataContext> metod, które nie zwracają zestawów wyników: takich jak INSERT, Updates i usunięć dla określonej klasy jednostki.

   Utwórz ten rodzaj metody <xref:System.Data.Linq.DataContext>, gdy aplikacja musi uruchamiać procedury składowane zamiast korzystać z domyślnego zachowania [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] do zapisywania zmodyfikowanych danych między klasą jednostki a bazą danych. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Zwracane typy metod DataContext

Podczas przeciągania procedur przechowywanych i funkcji z **Eksploratora serwera** lub **Eksplorator bazy danych** na **O/R Designer**, zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda zależy od tego, gdzie można upuścić elementu. Porzucenie elementów bezpośrednio do istniejącej klasy Entity tworzy metodę <xref:System.Data.Linq.DataContext> z typem zwracanym klasy Entity; upuszczanie elementów do pustego obszaru **projektanta o/R** (w obu okienka) tworzy metodę <xref:System.Data.Linq.DataContext>, która zwraca typ wygenerowany automatycznie. Typ wygenerowany automatycznie ma nazwę zgodną z nazwą procedury składowanej lub funkcją oraz właściwościami, które mapują do pól zwracanych przez procedurę składowaną lub funkcję.

> [!NOTE]
> Zwracany typ metody <xref:System.Data.Linq.DataContext> można zmienić po dodaniu jej do okienka metody. Aby sprawdzić lub zmienić zwracany typ metody <xref:System.Data.Linq.DataContext>, zaznacz ją i sprawdź Właściwość **zwracanego typu** w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [How to: zmiana zwracanego typu metody DataContext (Projektant O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Obiekty przeciągane z bazy danych na powierzchnię projektanta O/R są nazywane automatycznie, na podstawie nazw obiektów w bazie danych. Jeśli przeciągniesz ten sam obiekt więcej niż raz, do końca nowej nazwy zostanie dodany numer odróżniający nazwy. Gdy nazwy obiektów bazy danych zawierają spacje lub znaki nieobsługiwane w Visual Basic lub C#, spacja lub nieprawidłowy znak jest zastępowany podkreśleniem.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedury składowane](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Instrukcje: tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Przewodnik: dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
