---
title: Mapowanie klas LINQ to SQL do tabel/widoków (Projektant O-R)
description: Informacje o sposobie tworzenia klas jednostek LINQ to SQL (klasy, które są mapowane na tabele i widoki) w Object Relational Designer (Projektant O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 79e5c529c1aefb4777e174489fc8fd1ca95a4111
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436349"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Instrukcje: tworzenie klas LINQ do SQL zamapowanych na tabele i widoki (O/R Designer)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy, które są mapowane na tabele i widoki bazy danych, są nazywane *klasami jednostek*. Klasa jednostki mapuje do rekordu, natomiast poszczególne właściwości klasy jednostki są mapowane do poszczególnych kolumn, które składają się na rekord. Twórz klasy jednostek, które są oparte na tabelach lub widokach bazy danych, przeciągając tabele lub widoki z **Eksplorator serwera** lub **Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **Projektant O/R** generuje klasy i stosuje określone [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atrybuty w celu włączenia [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funkcjonalności (możliwości komunikacji i edycji danych <xref:System.Data.Linq.DataContext> ). Aby uzyskać szczegółowe informacje na temat [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klas, zobacz [model obiektów LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> **Projektant o/R** to proste mapowanie relacyjne obiektów, ponieważ obsługuje tylko 1:1 relacji mapowania. Innymi słowy, Klasa jednostki może mieć tylko skojarzenie mapowania 1:1 z tabelą lub widokiem bazy danych. Mapowanie złożone, takie jak mapowanie klasy jednostki na wiele tabel, nie jest obsługiwane. Można jednak zmapować klasę jednostki do widoku, który sprzęga wiele powiązanych tabel.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Tworzenie klas LINQ to SQL, które są mapowane do tabel lub widoków bazy danych

Przeciąganie tabel lub widoków z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta O/R** tworzy klasy jednostek oprócz <xref:System.Data.Linq.DataContext> metod, które są używane do przeprowadzania aktualizacji.

Domyślnie [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] środowisko uruchomieniowe tworzy logikę w celu zapisania zmian z klasy jednostki aktualizowalnej z powrotem do bazy danych. Ta logika jest oparta na schemacie tabeli (definicje kolumn i informacje o kluczu podstawowym). Jeśli to zachowanie nie jest potrzebne, można skonfigurować klasę jednostki, aby używać procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usuwania zamiast używania domyślnego [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowania w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Aby utworzyć klasy LINQ to SQL mapowane do tabel lub widoków bazy danych

1. W obszarze **serwer** lub **Eksplorator bazy danych** rozwiń węzeł **tabele** lub **widoki** i Znajdź tabelę lub widok bazy danych, który ma być używany w aplikacji.

2. Przeciągnij tabelę lub widok do **projektanta o/R**.

     Klasa jednostki jest tworzona i pojawia się na powierzchni projektowej. Klasa jednostki ma właściwości, które są mapowane na kolumny w zaznaczonej tabeli lub widoku.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Tworzenie źródła danych obiektu i wyświetlanie danych w formularzu

Po utworzeniu klas jednostek przy użyciu **projektanta O/R** można utworzyć źródło danych obiektu i wypełnić [okno źródła danych](add-new-data-sources.md#data-sources-window) z klasami jednostek.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Aby utworzyć źródło danych obiektu na podstawie LINQ to SQL klas jednostek

1. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie** , aby skompilować projekt.

2. Aby otworzyć okno **źródła danych** , w menu **dane** kliknij polecenie **Pokaż źródła danych**.

3. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

4. Kliknij pozycję **obiekt** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

5. Rozwiń węzły i Znajdź i wybierz klasę.

    > [!NOTE]
    > Jeśli Klasa **Customer** jest niedostępna, Anuluj działanie kreatora, Skompiluj projekt i ponownie uruchom kreatora.

6. Kliknij przycisk **Zakończ** , aby utworzyć źródło danych i dodać klasę jednostki **klienta** do okna **źródła danych** .

7. Przeciągnij elementy z okna **źródła danych** na formularz.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL model obiektów](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Przewodnik: dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Instrukcje: tworzenie skojarzenia (relacji) między klasami LINQ do SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
