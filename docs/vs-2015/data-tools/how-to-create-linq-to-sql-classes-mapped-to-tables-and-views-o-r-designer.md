---
title: 'Instrukcje: tworzenie klas LINQ to SQL mapowanych na tabele i widoki (Projektant O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665925"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Instrukcje: tworzenie klas LINQ to SQL mapowanych na tabele i widoki (Projektant O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Klasy LINQ to SQL mapowane na tabele i widoki bazy danych są nazywane *klasami jednostek*. Klasa jednostki mapuje do rekordu, natomiast poszczególne właściwości klasy jednostki są mapowane do poszczególnych kolumn, które składają się na rekord. Twórz klasy jednostek, które są oparte na tabelach lub widokach bazy danych, przeciągając tabele lub widoki z **Eksplorator serwera** /**Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). @No__t_0 generuje klasy i stosuje określony [! LINQ to SQL atrybuty umożliwiające włączenie [! Funkcja LINQ to SQL (możliwości komunikacji i edycji danych <xref:System.Data.Linq.DataContext>). Aby uzyskać szczegółowe informacje na temat [! LINQ to SQL klasy, zobacz [LINQ to SQL modelu obiektów](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> @No__t_0 to proste mapowanie relacyjne obiektów, ponieważ obsługuje tylko 1:1 relacji mapowania. Innymi słowy, Klasa jednostki może mieć tylko skojarzenie mapowania 1:1 z tabelą lub widokiem bazy danych. Mapowanie złożone, takie jak mapowanie klasy jednostki na wiele tabel, nie jest obsługiwane. Można jednak zmapować klasę jednostki do widoku, który sprzęga wiele powiązanych tabel.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Tworzenie klas LINQ to SQL, które są mapowane do tabel lub widoków bazy danych
 Przeciąganie tabel lub widoków z **Eksplorator serwera** /**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tworzy klasy jednostek oprócz metod <xref:System.Data.Linq.DataContext>, które są używane do przeprowadzania aktualizacji.

 Domyślnie [! Środowisko uruchomieniowe LINQ to SQL tworzy logikę umożliwiającą zapisanie zmian z klasy jednostki aktualizowalnej z powrotem do bazy danych. Ta logika jest oparta na schemacie tabeli (definicje kolumn i informacje o kluczu podstawowym). Jeśli to zachowanie nie jest potrzebne, można skonfigurować klasę jednostki, aby używać procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usuwania zamiast używać wartości domyślnej [! Zachowanie LINQ to SQL środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Aby utworzyć klasy LINQ to SQL mapowane do tabel lub widoków bazy danych

1. W**Eksplorator bazy danych** **serwer** / rozwiń węzeł **tabele** lub **widoki** i Znajdź tabelę lub widok bazy danych, który ma być używany w aplikacji.

2. Przeciągnij tabelę lub widok na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Klasa jednostki jest tworzona i pojawia się na powierzchni projektowej. Klasa jednostki ma właściwości, które są mapowane na kolumny w zaznaczonej tabeli lub widoku.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Tworzenie źródła danych obiektu i wyświetlanie danych w formularzu
 Po utworzeniu klas jednostek przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] można utworzyć źródło danych obiektu i wypełnić [okno źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) z klasami jednostek.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Aby utworzyć źródło danych obiektu na podstawie LINQ to SQL klas jednostek

1. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie** , aby skompilować projekt.

2. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

3. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

4. Kliknij pozycję **obiekt** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

5. Rozwiń węzły i Znajdź i wybierz klasę.

    > [!NOTE]
    > Jeśli Klasa **Customer** jest niedostępna, Anuluj działanie kreatora, Skompiluj projekt i ponownie uruchom kreatora.

6. Kliknij przycisk **Zakończ** , aby utworzyć źródło danych i dodać klasę jednostki **klienta** do okna **źródła danych** .

7. Przeciągnij elementy z okna **źródła danych** na formularz.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Model obiektu LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Przewodnik: dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Wskazówki: Dodawanie walidacji do klas jednostek](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Instrukcje: tworzenie skojarzenia (relacji) między klasami LINQ do SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)