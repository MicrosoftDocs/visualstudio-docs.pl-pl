---
title: Tworzenie i konfigurowanie zestawów danych
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b71d4b8ea58cbbe36e3fe48228789d4aee02af53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567795"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Tworzenie i konfigurowanie zestawów danych w programie Visual Studio

Zestaw danych to zbiór obiektów, które przechowuje dane z bazy danych w pamięci i obsługuje śledzenie zmian, aby umożliwić tworzenie, Odczyt, aktualizowanie i usuwanie operacji (CRUD) na tych danych bez konieczności zawsze być połączone z bazą danych. Zestawy danych zostały zaprojektowane dla prostej *formularzy nad danymi* aplikacji biznesowych. W przypadku nowych aplikacji należy wziąć pod uwagę przy użyciu platformy Entity Framework do przechowywania i modelowania danych w pamięci. Aby pracować z zestawami danych, należy mieć podstawową wiedzę na temat pojęć dotyczących baz danych.

Możesz utworzyć typizowany <xref:System.Data.DataSet> klasy w programie Visual Studio w czasie projektowania za pomocą **Kreatora konfiguracji źródła danych**. Aby uzyskać informacji na temat programowe tworzenie zestawów danych, zobacz [Tworzenie zestawu danych (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Utwórz nowy zestaw danych za pomocą Kreatora konfiguracji źródła danych

1. Otwórz projekt w programie Visual Studio, a następnie wybierz **projektu** > **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

2. Wybierz typ źródła danych, z którą będzie łączyć.

     ![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png)

3. Wybierz bazę danych lub bazy danych, które będą znajdować się źródło danych dla zestawu danych.

     ![Źródła danych wybierz połączenie](../data-tools/media/data-source-choose-a-connection.png)

4. Wybierz tabele (lub poszczególnych kolumn), procedur przechowywanych, funkcji i widoków z bazy danych, który ma być reprezentowane w zestawie danych.

     ![Wybierz obiekty bazy danych](../data-tools/media/raddata-chose-objects.png)

5. Kliknij przycisk **Zakończ**.

   Zestaw danych jest widoczny jako węzeł w **Eksploratora rozwiązań**.

   ![Zestaw danych w Eksploratorze rozwiązań](../data-tools/media/dataset-in-solution-explorer.png)

6. Kliknij węzeł zestawu danych w **Eksploratora rozwiązań** można otworzyć zestawu danych w **Projektanta obiektów DataSet**. Każda tabela w zestawie danych ma skojarzoną `TableAdapter` obiektu, który jest reprezentowany w dolnej części. Karta tabeli jest używany do wypełniania zestawu danych i, opcjonalnie, wysyłanie poleceń do bazy danych.

   ![Projektant obiektów DataSet](../data-tools/media/dataset-designer.png)

7. Wierszy relacji, które łączą się z tabel reprezentują relacje między tabelami, zgodnie z definicją w bazie danych. Domyślnie ograniczenia klucza obcego w bazie danych są reprezentowane jako relacja tylko przy użyciu aktualizacji i usuwania reguł ustawiony na wartość none. Zazwyczaj jest to czego chcesz. Jednak można kliknąć wiersze, aby wyświetlić **relacji** okno dialogowe, w którym można zmienić zachowanie aktualizacji hierarchicznych. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md) i [hierarchiczna aktualizacja](../data-tools/hierarchical-update.md).

     ![Okno dialogowe Zestaw danych relacji](../data-tools/media/raddata-relation-dialog.png)

8. Kliknij tabelę, tabeli karty lub nazwa kolumny w tabeli, aby wyświetlić jego właściwości w **właściwości** okna. Można zmodyfikować niektóre wartości w tym miejscu. Pamiętaj tylko, modyfikowania zestawu danych, a nie źródłowej bazy danych.

     ![Właściwości kolumny zestawu danych](../data-tools/media/dataset-column-properties.png)

9. Możesz dodać nowe tabele lub adapterów tabel do zestawu danych lub dodawanie nowych zapytań do istniejących adapterów tabel lub określić nowe relacje między tabelami, przeciągając tych elementów z **przybornika** kartę. Ta karta jest wyświetlana, gdy **Projektanta obiektów DataSet** jest w trybie koncentracji uwagi.

     ![Przybornik zestawu danych](../data-tools/media/raddata-dataset-toolbox.png)

Następnie można określić sposobu wypełniania zestawu danych z danymi. W tym używasz **Kreator konfiguracji TableAdapter**. Aby uzyskać więcej informacji, zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Dodaj tabelę bazy danych lub inny obiekt do istniejącego zestawu danych

Ta procedura pokazuje, jak dodać tabelę z tej samej bazy danych, którego użyto do utworzenia zestawu danych.

1. Kliknij węzeł zestawu danych w **Eksploratora rozwiązań** celu **Projektanta obiektów DataSet** do zespołu.

2. Kliknij przycisk **źródeł danych** kartę na lewym marginesie programu Visual Studio lub typ **źródeł danych** w polu wyszukiwania.

3. Kliknij prawym przyciskiem myszy węzeł zestawu danych, a następnie wybierz pozycję **Konfigurowanie źródła danych za pomocą kreatora**.

     ![Menu kontekstowe źródła danych](../data-tools/media/data-source-context-menu.png)

4. Użyj kreatora, aby określić które dodatkowych tabel, procedur składowanych lub innych obiektów bazy danych, aby dodać do zestawu danych.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Dodaj tabelę danych autonomicznej do zestawu danych

1. Otwórz swój zestaw danych w **Projektanta obiektów Dataset**.

2. Przeciągnij <xref:System.Data.DataTable> klasy z **DataSet** karcie **przybornika** na **Projektanta obiektów Dataset**.

3. Dodawanie kolumn do definiowania tabeli danych. Kliknij prawym przyciskiem myszy w tabeli, a następnie wybierz **Dodaj** > **kolumny**. Użyj **właściwości** okna, aby ustawić typ danych kolumny i kluczem, jeśli to konieczne.

Tabele autonomicznej konieczne wdrożenie `Fill` logiki w tabelach autonomicznej tak, aby wypełnić je danymi. Instrukcje dotyczące Wypełnianie tabel danych autonomicznych, zobacz [wypełnianie zestawu danych z elementu DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)