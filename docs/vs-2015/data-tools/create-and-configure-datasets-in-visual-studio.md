---
title: Tworzenie i konfigurowanie zestawów danych
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6864708d3e60898b32ba07b14939a5c3e31d897e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705134"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Tworzenie i konfigurowanie zestawów danych w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *dataset* to zbiór obiektów, które przechowuje dane z bazy danych w pamięci i obsługuje śledzenie zmian, aby umożliwić tworzenie, Odczyt, aktualizowanie i usuwanie operacji (CRUD) na tych danych bez konieczności zawsze być połączone z bazą danych. Zestawy danych zostały zaprojektowane dla prostej *formularzy nad danymi* aplikacji biznesowych. W przypadku nowych aplikacji należy wziąć pod uwagę przy użyciu platformy Entity Framework do przechowywania i modelowania danych w pamięci. Aby pracować z zestawami danych, należy mieć podstawową wiedzę na temat pojęć dotyczących baz danych.

 Możesz utworzyć typizowany <xref:System.Data.DataSet> klasy w programie Visual Studio w czasie projektowania za pomocą **Kreatora konfiguracji źródła danych**. Aby uzyskać informacji na temat programowe tworzenie zestawów danych, zobacz [Tworzenie zestawu danych](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Utwórz nowy zestaw danych za pomocą Kreatora konfiguracji źródła danych

1. Na **projektu** menu, kliknij przycisk **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

2. Wybierz typ źródła danych, które będą łączyć się.

     ![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png "Kreatora konfiguracji źródła danych")

3. W przypadku baz danych wybierz bazę danych lub bazy danych, które będą znajdować się źródło danych dla zestawu danych.

     ![Źródła danych wybierz połączenie](../data-tools/media/data-source-choose-a-connection.png "źródła danych wybierz połączenie")

4. Wybierz tabele (lub poszczególnych kolumn), procedur przechowywanych, funkcji i widoków z bazy danych, który ma być reprezentowane w zestawie danych.

     ![Wybierz obiekty bazy danych](../data-tools/media/raddata-chose-objects.png "raddata wybranego obiektów")

5. Kliknij przycisk **Zakończ**.

6. Zestaw danych jest widoczny jako węzeł w **Eksploratora rozwiązań**:

     ![Zestaw danych w Eksploratorze rozwiązań](../data-tools/media/dataset-in-solution-explorer.png "zestawu danych w Eksploratorze rozwiązań")

     Kliknij ten węzeł, a zestaw danych jest wyświetlana w **Projektanta obiektów DataSet**. Należy pamiętać, że każda tabela w zestawie danych ma skojarzony obiekt TableAdapter, który jest reprezentowany w dolnej części. Karta tabeli jest używany do wypełniania zestawu danych i, opcjonalnie, wysyłanie poleceń do bazy danych.

     ![Projektant obiektów DataSet](../data-tools/media/dataset-designer.png "Projektanta obiektów DataSet")

7. Wierszy relacji, które łączą się z tabel reprezentują relacje między tabelami, zgodnie z definicją w bazie danych. Domyślnie ograniczenia klucza obcego w bazie danych są reprezentowane jako relacja tylko przy użyciu aktualizacji i usuwania reguł ustawiony na wartość none. Zazwyczaj jest to czego chcesz. Jednak można kliknąć wiersze, aby wyświetlić **relacji** okno dialogowe, w którym można zmienić zachowanie aktualizacji hierarchicznych. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md) i [hierarchiczna aktualizacja](../data-tools/hierarchical-update.md).

     ![Okno dialogowe Zestaw danych relacji](../data-tools/media/raddata-relation-dialog.png "raddata relacji w oknie dialogowym")

8. Kliknij tabelę, tabeli karty lub nazwa kolumny w tabeli, aby wyświetlić jego właściwości w **właściwości** okna. Można zmodyfikować niektóre wartości w tym miejscu. Pamiętaj tylko, modyfikowania zestawu danych, a nie źródłowej bazy danych.

     ![Właściwości kolumny zestawu danych](../data-tools/media/dataset-column-properties.png "właściwości kolumny zestawu danych")

9. Możesz dodać nowe tabele lub adapterów tabel do zestawu danych lub dodawanie nowych zapytań do istniejących adapterów tabel lub określić nowe relacje między tabelami, przeciągając tych elementów z **przybornika** kartę. Ta karta jest wyświetlana, gdy **Projektanta obiektów DataSet** jest w trybie koncentracji uwagi.

     ![Przybornik zestawu danych](../data-tools/media/raddata-dataset-toolbox.png "raddata Przybornik zestawu danych")

10. Następnie użytkownik najprawdopodobniej wskazane będzie określenie sposobu wypełniania zestawu danych z danymi. W tym używasz **Kreator konfiguracji TableAdapter**. Aby uzyskać więcej informacji, zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Dodaj tabelę bazy danych lub inny obiekt do istniejącego zestawu danych
 Ta procedura pokazuje, jak dodać tabelę z tej samej bazy danych, którego użyto do utworzenia zestawu danych.

1. Kliknij węzeł zestawu danych w **Eksploratora rozwiązań** zapewnić Projektanta obiektów DataSet fokus.

2. Kliknij przycisk **źródeł danych** kartę na lewym marginesie programu Visual Studio, lub wprowadź `Data Sources` w **szybkiego uruchamiania**.

3. Kliknij prawym przyciskiem myszy węzeł zestawu danych, a następnie wybierz pozycję **Konfigurowanie źródła danych za pomocą kreatora** .

     ![Menu kontekstowe źródła danych](../data-tools/media/data-source-context-menu.png "menu kontekstowe źródła danych")

4. Użyj kreatora, aby określić, które dodatkowe tabele lub procedur składowanych lub innego obiektu bazy danych, aby dodać do zestawu danych.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Dodaj tabelę danych autonomicznej do zestawu danych

1. Otwórz swój zestaw danych w **Projektanta obiektów Dataset**.

2. Przeciągnij <xref:System.Data.DataTable> klasy z **DataSet** karcie **przybornika** na **Projektanta obiektów Dataset**.

3. Dodawanie kolumn do definiowania tabeli danych. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kolumn do DataTable](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Tabele autonomicznej konieczne wdrożenie `Fill` logiki w tabelach autonomicznej tak, aby wypełnić je danymi. Instrukcje dotyczące Wypełnianie tabel danych autonomicznych, zobacz [wypełnianie zestawu danych z elementu DataAdapter](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
