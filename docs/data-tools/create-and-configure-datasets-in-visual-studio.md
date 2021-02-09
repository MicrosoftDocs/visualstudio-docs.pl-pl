---
title: Tworzenie i konfigurowanie zestawów danych
description: Tworzenie i konfigurowanie zestawów danych w programie Visual Studio. Zestaw danych to zbiór obiektów, które przechowują dane z bazy danych w pamięci i obsługują operacje CRUD na tych danych.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f625b17841fe63b0c42dcfb82c2e859d6406e776
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859128"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Instrukcje: Tworzenie i konfigurowanie zestawów danych w programie Visual Studio

Zestaw danych to zbiór obiektów, które przechowują dane z bazy danych w pamięci i obsługują śledzenie zmian, aby umożliwić wykonywanie operacji tworzenia, odczytu, aktualizacji i usuwania (CRUD) na tych danych bez konieczności ciągłego połączenia z bazą danych. Zestawy danych zostały zaprojektowane na potrzeby prostych *formularzy* dla aplikacji firmowych. W przypadku nowych aplikacji należy rozważyć użycie Entity Framework do przechowywania i modelowania danych w pamięci. Aby można było korzystać z zestawów danych, należy uzyskać podstawową wiedzę na temat pojęć związanych z bazami informacji.

Można utworzyć klasę o określonym typie <xref:System.Data.DataSet> w programie Visual Studio w czasie projektowania przy użyciu **Kreatora konfiguracji źródła danych**. Aby uzyskać informacje na temat tworzenia zestawów danych programowo, zobacz [Creating a DataSet (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Tworzenie nowego zestawu danych za pomocą Kreatora konfiguracji źródła danych

1. Otwórz projekt w programie Visual Studio, a następnie wybierz pozycję **projekt**  >  **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

2. Wybierz typ źródła danych, z którym będziesz się łączyć.

     ![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png)

3. Wybierz bazę danych lub bazy danych, które będą źródłem danych dla zestawu danych.

     ![Wybierz połączenie ze źródłem danych](../data-tools/media/data-source-choose-a-connection.png)

4. Wybierz tabele (lub pojedyncze kolumny), procedury składowane, funkcje i widoki z bazy danych, która ma być reprezentowana w zestawie danych.

     ![Wybierz obiekty bazy danych](../data-tools/media/raddata-chose-objects.png)

5. Kliknij przycisk **Finish** (Zakończ).

   Zestaw danych jest wyświetlany jako węzeł w **Eksplorator rozwiązań**.

   ![Zestaw danych w Eksplorator rozwiązań](../data-tools/media/dataset-in-solution-explorer.png)

6. Kliknij węzeł zestaw danych w **Eksplorator rozwiązań** , aby otworzyć zestaw danych w **Projektancie obiektów DataSet**. Każda tabela w zestawie danych ma skojarzony `TableAdapter` obiekt, który jest reprezentowany u dołu. Karta tabeli służy do wypełniania zestawu danych i opcjonalnego wysyłania poleceń do bazy danych.

   ![Projektant obiektów DataSet](../data-tools/media/dataset-designer.png)

7. Linie relacji łączące tabele reprezentują relacje między tabelami, zgodnie z definicją w bazie danych. Domyślnie ograniczenia klucza obcego w bazie danych są reprezentowane tylko jako relacja, a reguły aktualizacji i usuwania mają wartość none. Zwykle jest to to, czego potrzebujesz. Można jednak kliknąć linie, aby wyświetlić okno dialogowe **relacji** , w którym można zmienić zachowanie hierarchicznych aktualizacji. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md) i [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md).

     ![Okno dialogowe relacji zestawu danych](../data-tools/media/raddata-relation-dialog.png)

8. Kliknij tabelę, kartę tabeli lub nazwę kolumny w tabeli, aby wyświetlić jej właściwości w oknie **Właściwości** . Niektóre wartości można modyfikować w tym miejscu. Pamiętaj, że modyfikujesz zestaw danych, a nie źródłową bazę danych.

     ![Właściwości kolumny DataSet](../data-tools/media/dataset-column-properties.png)

9. Możesz dodać nowe tabele lub karty tabel do zestawu danych lub dodać nowe zapytania dla istniejących kart tabel lub określić nowe relacje między tabelami, przeciągając te elementy z karty **Przybornik** . Ta karta pojawia się, gdy **Projektant obiektów DataSet** jest fokusem.

     ![Przybornik zestawu danych](../data-tools/media/raddata-dataset-toolbox.png)

Następnie możesz chcieć określić sposób wypełniania zestawu danych danymi. W tym celu należy użyć **Kreatora konfiguracji TableAdapter**. Aby uzyskać więcej informacji, zobacz [Wypełnij zestawy danych za pomocą TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Dodawanie tabeli bazy danych lub innego obiektu do istniejącego zestawu danych

Ta procedura pokazuje, jak dodać tabelę z tej samej bazy danych, która została użyta do utworzenia zestawu danych.

1. Kliknij węzeł zestaw danych w **Eksplorator rozwiązań** , aby przenieść **projektanta obiektów DataSet** do fokusu.

2. Kliknij kartę **źródła danych** na lewym marginesie programu Visual Studio lub wpisz **źródła danych** w polu wyszukiwania.

3. Kliknij prawym przyciskiem myszy węzeł zestaw danych i wybierz polecenie **Konfiguruj źródło danych za pomocą Kreatora**.

     ![Menu kontekstowe źródła danych](../data-tools/media/data-source-context-menu.png)

4. Użyj kreatora, aby określić, które dodatkowe tabele, procedury składowane lub inne obiekty bazy danych mają być dodane do zestawu danych.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Dodawanie autonomicznej tabeli danych do zestawu danych

1. Otwórz zestaw danych w **Projektant obiektów DataSet**.

2. Przeciągnij <xref:System.Data.DataTable> klasę z karty **zestaw danych** **przybornika** na **Projektant obiektów DataSet**.

3. Dodaj kolumny, aby zdefiniować tabelę danych. Kliknij prawym przyciskiem myszy tabelę i wybierz polecenie **Dodaj**  >  **kolumnę**. Użyj okna **Właściwości** , aby ustawić typ danych kolumny i klucza w razie potrzeby.

Tabele autonomiczne muszą implementować `Fill` logikę w tabelach autonomicznych, dzięki czemu można wypełniać je danymi. Aby uzyskać informacje na temat wypełniania tabel danych autonomicznych, zobacz [zapełnianie zestawu danych z elementu DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Zobacz też

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
