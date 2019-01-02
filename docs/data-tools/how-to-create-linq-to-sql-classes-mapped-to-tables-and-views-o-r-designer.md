---
title: 'Instrukcje: Tworzenie typu LINQ do klas SQL zamapowanych na tabele i widoki (Projektant O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b011ccd782a270eb770a77683db62dadbb66d223
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844304"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Instrukcje: Tworzenie typu LINQ do klas SQL zamapowanych na tabele i widoki (O/R Designer)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy, które są mapowane do bazy danych, tabele i widoki są nazywane *klas jednostek*. Klasa jednostki mapuje rekord, podczas gdy poszczególne właściwości klasy jednostki mapują do poszczególnych kolumn, które tworzą rekord. Tworzenie klas jednostek, które są oparte na bazy danych tabel lub widoków, przeciągając tabele lub widoki z **Eksploratora serwera** lub **Eksplorator bazy danych** na [LINQ to SQL tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **O/R Designer** generuje klasy, a następnie stosuje konkretne [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atrybutów, aby umożliwić [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funkcji (łączności danych i możliwości edytowania <xref:System.Data.Linq.DataContext>). Aby uzyskać szczegółowe informacje na temat [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klas, zobacz [LINQ to SQL model obiektów](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> **O/R Designer** jest mapowania relacyjnych prostego obiektu, ponieważ obsługuje on tylko relacji mapowanie 1:1. Innymi słowy klasa jednostka może mieć tylko relacji mapowanie 1:1 z tabeli bazy danych lub widoku. Mapowanie złożonych, takie jak mapowanie klasę jednostki z wieloma tabelami, nie jest obsługiwane. Jednak można mapować klasę jednostki, do widoku, który łączy się wieloma powiązanymi tabelami.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Tworzenie typu LINQ to SQL klas, które są mapowane do bazy danych tabel lub widoków

Przeciąganie tabele lub widoki z **Eksploratora serwera** lub **Eksplorator bazy danych** na **O/R Designer** tworzy klas jednostek oprócz <xref:System.Data.Linq.DataContext> metody, są używane do przeprowadzania aktualizacji.

Domyślnie [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] środowisko uruchomieniowe tworzy logiki, aby zapisać zmiany z klasy można aktualizować jednostek w bazie danych. Tę logikę opiera się na schemat tabeli (definicje kolumn i informacje o kluczu podstawowym). Jeśli nie chcesz tego zachowania, można skonfigurować klasę jednostki, na używanie procedur składowanych do wykonywania operacji wstawienia, aktualizacje i usunięcia, a nie przy użyciu domyślnego [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowania w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Aby tworzyć LINQ do klas SQL, które są mapowane do bazy danych tabel lub widoków

1.  W **serwera** lub **Eksplorator bazy danych**, rozwiń **tabel** lub **widoków** i Znajdź w tabeli bazy danych lub wyświetlić chcesz używać w sieci aplikacja.

2.  Przeciągnij tabelę lub wyświetlić na **O/R Designer**.

     Klasa jednostki zostanie utworzony i wyświetlony na powierzchni projektowej. Klasa jednostki ma właściwości, które mapują do kolumn w wybranej tabeli lub widoku.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Tworzenie obiektu źródła danych i wyświetlić dane w formularzu

Po utworzeniu klas jednostek za pomocą **O/R Designer**, można utworzyć źródło danych obiektu i wypełnić [okna źródeł danych](add-new-data-sources.md#data-sources-window) przy użyciu klas jednostek.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Aby utworzyć źródło danych obiektu opartego na LINQ do SQL klas jednostek

1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie** do kompilowania projektu.

2.  Aby otworzyć **źródeł danych** okna na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

3.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

4.  Kliknij przycisk **obiektu** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.

5.  Rozwiń węzły, a następnie znajdź i wybierz klasy.

    > [!NOTE]
    > Jeśli **klienta** klasy nie jest dostępna, Anuluj kreatora, skompiluj projekt i uruchom ponownie kreatora.

6.  Kliknij przycisk **Zakończ** Utwórz źródło danych i dodać **klienta** klasy jednostki **źródeł danych** okna.

7.  Przeciągnij elementy z **źródeł danych** okna w formularzu.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: Tworzenie zapytań LINQ do klas SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL model obiektów](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Przewodnik: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Instrukcje: Utwórz skojarzenie (Relacja) między LINQ to SQL klas (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)