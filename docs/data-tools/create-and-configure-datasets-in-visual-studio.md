---
title: Tworzenie i konfigurowanie zestawów danych
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8222b1985ab7f765be9b06fdd6abf7cb1e1cb2dc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586916"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Instrukcje: Tworzenie i konfigurowanie zestawów danych w programie Visual Studio

Zestaw danych to zbiór obiektów, które przechowują dane z bazy danych w pamięci i obsługują śledzenie zmian, aby umożliwić wykonywanie operacji tworzenia, odczytu, aktualizacji i usuwania (CRUD) na tych danych bez konieczności ciągłego połączenia z bazą danych. Zestawy danych zostały zaprojektowane dla prostej *formularzy nad danymi* aplikacji biznesowych. W przypadku nowych aplikacji należy wziąć pod uwagę przy użyciu platformy Entity Framework do przechowywania i modelowania danych w pamięci. Aby pracować z zestawami danych, należy mieć podstawową wiedzę na temat pojęć dotyczących baz danych.

Można utworzyć wpisaną klasę <xref:System.Data.DataSet> w programie Visual Studio w czasie projektowania przy użyciu **Kreatora konfiguracji źródła danych**. Aby uzyskać informacje na temat tworzenia zestawów danych programowo, zobacz [Creating a DataSet (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Utwórz nowy zestaw danych za pomocą Kreatora konfiguracji źródła danych

1. Otwórz projekt w programie Visual Studio, a następnie wybierz pozycję **projekt** > **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

2. Wybierz typ źródła danych, z którym będziesz się łączyć.

     ![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png)

3. Wybierz bazę danych lub bazy danych, które będą źródłem danych dla zestawu danych.

     ![Wybierz połączenie ze źródłem danych](../data-tools/media/data-source-choose-a-connection.png)

4. Wybierz tabele (lub poszczególnych kolumn), procedur przechowywanych, funkcji i widoków z bazy danych, który ma być reprezentowane w zestawie danych.

     ![Wybierz obiekty bazy danych](../data-tools/media/raddata-chose-objects.png)

5. Kliknij przycisk **Zakończ**.

   Zestaw danych jest wyświetlany jako węzeł w **Eksplorator rozwiązań**.

   ![Zestaw danych w Eksplorator rozwiązań](../data-tools/media/dataset-in-solution-explorer.png)

6. Kliknij węzeł zestaw danych w **Eksplorator rozwiązań** , aby otworzyć zestaw danych w **Projektancie obiektów DataSet**. Każda tabela w zestawie danych ma skojarzony obiekt `TableAdapter`, który jest reprezentowany u dołu. Karta tabeli jest używany do wypełniania zestawu danych i, opcjonalnie, wysyłanie poleceń do bazy danych.

   ![Projektant obiektów DataSet](../data-tools/media/dataset-designer.png)

7. Wierszy relacji, które łączą się z tabel reprezentują relacje między tabelami, zgodnie z definicją w bazie danych. Domyślnie ograniczenia klucza obcego w bazie danych są reprezentowane jako relacja tylko przy użyciu aktualizacji i usuwania reguł ustawiony na wartość none. Zazwyczaj jest to czego chcesz. Można jednak kliknąć linie, aby wyświetlić okno dialogowe **relacji** , w którym można zmienić zachowanie hierarchicznych aktualizacji. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md) i [hierarchiczna aktualizacja](../data-tools/hierarchical-update.md).

     ![Okno dialogowe relacji zestawu danych](../data-tools/media/raddata-relation-dialog.png)

8. Kliknij tabelę, tabeli karty lub nazwa kolumny w tabeli, aby wyświetlić jego właściwości w **właściwości** okna. Można zmodyfikować niektóre wartości w tym miejscu. Pamiętaj tylko, modyfikowania zestawu danych, a nie źródłowej bazy danych.

     ![Właściwości kolumny DataSet](../data-tools/media/dataset-column-properties.png)

9. Możesz dodać nowe tabele lub karty tabel do zestawu danych lub dodać nowe zapytania dla istniejących kart tabel lub określić nowe relacje między tabelami, przeciągając te elementy z karty **Przybornik** . Ta karta pojawia się, gdy **Projektant obiektów DataSet** jest fokusem.

     ![Przybornik zestawu danych](../data-tools/media/raddata-dataset-toolbox.png)

Następnie możesz chcieć określić sposób wypełniania zestawu danych danymi. W tym używasz **Kreator konfiguracji TableAdapter**. Aby uzyskać więcej informacji, zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Dodaj tabelę bazy danych lub inny obiekt do istniejącego zestawu danych

Ta procedura pokazuje, jak dodać tabelę z tej samej bazy danych, którego użyto do utworzenia zestawu danych.

1. Kliknij węzeł zestaw danych w **Eksplorator rozwiązań** , aby przenieść **projektanta obiektów DataSet** do fokusu.

2. Kliknij kartę **źródła danych** na lewym marginesie programu Visual Studio lub wpisz **źródła danych** w polu wyszukiwania.

3. Kliknij prawym przyciskiem myszy węzeł zestaw danych i wybierz polecenie **Konfiguruj źródło danych za pomocą Kreatora**.

     ![Menu kontekstowe źródła danych](../data-tools/media/data-source-context-menu.png)

4. Użyj kreatora, aby określić, które dodatkowe tabele, procedury składowane lub inne obiekty bazy danych mają być dodane do zestawu danych.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Dodaj tabelę danych autonomicznej do zestawu danych

1. Otwórz swój zestaw danych w **Projektanta obiektów Dataset**.

2. Przeciągnij <xref:System.Data.DataTable> klasy z **DataSet** karcie **przybornika** na **Projektanta obiektów Dataset**.

3. Dodawanie kolumn do definiowania tabeli danych. Kliknij prawym przyciskiem myszy tabelę i wybierz polecenie **dodaj** > **kolumnę**. Użyj okna **Właściwości** , aby ustawić typ danych kolumny i klucza w razie potrzeby.

Tabele autonomicznej konieczne wdrożenie `Fill` logiki w tabelach autonomicznej tak, aby wypełnić je danymi. Instrukcje dotyczące Wypełnianie tabel danych autonomicznych, zobacz [wypełnianie zestawu danych z elementu DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
