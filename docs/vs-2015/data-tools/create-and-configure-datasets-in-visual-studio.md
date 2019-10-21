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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631202"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Tworzenie i konfigurowanie zestawów danych w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw *danych* to zbiór obiektów, które przechowują dane z bazy danych w pamięci i obsługują śledzenie zmian, aby umożliwić wykonywanie operacji tworzenia, odczytu, aktualizacji i usuwania (CRUD) na tych danych bez konieczności ciągłego połączenia z bazą danych. Zestawy danych zostały zaprojektowane na potrzeby prostych *formularzy* dla aplikacji firmowych. W przypadku nowych aplikacji należy rozważyć użycie Entity Framework do przechowywania i modelowania danych w pamięci. Aby można było korzystać z zestawów danych, należy uzyskać podstawową wiedzę na temat pojęć związanych z bazami informacji.

 Można utworzyć wpisaną klasę <xref:System.Data.DataSet> w programie Visual Studio w czasie projektowania przy użyciu **Kreatora konfiguracji źródła danych**. Aby uzyskać informacje na temat tworzenia zestawów danych programowo, zobacz [Creating a DataSet](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Tworzenie nowego zestawu danych za pomocą Kreatora konfiguracji źródła danych

1. W menu **projekt** kliknij polecenie **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

2. Wybierz typ źródła danych, z którym będziesz się łączyć.

     ![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png "Kreator konfiguracji źródła danych")

3. W obszarze bazy danych wybierz bazę danych lub bazy danych, które będą źródłem danych dla zestawu danych.

     ![Wybierz połączenie ze źródłem danych](../data-tools/media/data-source-choose-a-connection.png "Wybierz połączenie ze źródłem danych")

4. Wybierz tabele (lub pojedyncze kolumny), procedury składowane, funkcje i widoki z bazy danych, która ma być reprezentowana w zestawie danych.

     ![Wybierz obiekty bazy danych](../data-tools/media/raddata-chose-objects.png "raddata wybrane obiekty")

5. Kliknij przycisk **Zakończ**.

6. Zestaw danych jest wyświetlany jako węzeł w **Eksplorator rozwiązań**:

     ![Zestaw danych w Eksplorator rozwiązań](../data-tools/media/dataset-in-solution-explorer.png "Zestaw danych w Eksplorator rozwiązań")

     Kliknij ten węzeł, a zestaw danych pojawi się w **Projektancie obiektów DataSet**. Zwróć uwagę, że każda tabela w zestawie danych ma skojarzony obiekt TableAdapter, który jest reprezentowany u dołu. Karta tabeli służy do wypełniania zestawu danych i opcjonalnego wysyłania poleceń do bazy danych.

     ![Projektant obiektów DataSet](../data-tools/media/dataset-designer.png "Projektant obiektów DataSet")

7. Linie relacji łączące tabele reprezentują relacje między tabelami, zgodnie z definicją w bazie danych. Domyślnie ograniczenia klucza obcego w bazie danych są reprezentowane tylko jako relacja, a reguły aktualizacji i usuwania mają wartość none. Zwykle jest to to, czego potrzebujesz. Można jednak kliknąć linie, aby wyświetlić okno dialogowe **relacji** , w którym można zmienić zachowanie hierarchicznych aktualizacji. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md) i [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md).

     ![Okno dialogowe relacji zestawu danych](../data-tools/media/raddata-relation-dialog.png "okno dialogowe relacji raddata")

8. Kliknij tabelę, kartę tabeli lub nazwę kolumny w tabeli, aby wyświetlić jej właściwości w oknie **Właściwości** . Niektóre wartości można modyfikować w tym miejscu. Pamiętaj, że modyfikujesz zestaw danych, a nie źródłową bazę danych.

     ![Właściwości kolumny DataSet](../data-tools/media/dataset-column-properties.png "Właściwości kolumny DataSet")

9. Możesz dodać nowe tabele lub karty tabel do zestawu danych lub dodać nowe zapytania dla istniejących kart tabel lub określić nowe relacje między tabelami, przeciągając te elementy z karty **Przybornik** . Ta karta pojawia się, gdy **Projektant obiektów DataSet** jest fokusem.

     ![Przybornik zestawu danych](../data-tools/media/raddata-dataset-toolbox.png "Przybornik zestawu danych raddata")

10. Następnie prawdopodobnie chcesz określić sposób wypełniania zestawu danych danymi. W tym celu należy użyć **Kreatora konfiguracji TableAdapter**. Aby uzyskać więcej informacji, zobacz [Wypełnij zestawy danych za pomocą TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Dodawanie tabeli bazy danych lub innego obiektu do istniejącego zestawu danych
 Ta procedura pokazuje, jak dodać tabelę z tej samej bazy danych, która została użyta do utworzenia zestawu danych.

1. Kliknij węzeł zestaw danych w **Eksplorator rozwiązań** , aby przenieść projektanta obiektów DataSet do fokusu.

2. Kliknij kartę **źródła danych** na lewym marginesie programu Visual Studio lub wprowadź `Data Sources` w obszarze **szybkiego uruchamiania**.

3. Kliknij prawym przyciskiem myszy węzeł zestaw danych i wybierz polecenie **Konfiguruj źródło danych za pomocą Kreatora** .

     ![Menu kontekstowe źródła danych](../data-tools/media/data-source-context-menu.png "Menu kontekstowe źródła danych")

4. Użyj kreatora, aby określić, które dodatkowe tabele lub inne obiekty bazy danych mają zostać dodane do zestawu danych.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Dodawanie autonomicznej tabeli danych do zestawu danych

1. Otwórz zestaw danych w **Projektant obiektów DataSet**.

2. Przeciągnij klasę <xref:System.Data.DataTable> z karty **zestaw danych** **przybornika** na **Projektant obiektów DataSet**.

3. Dodaj kolumny, aby zdefiniować tabelę danych. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Dodawanie kolumn do tabeli DataTable](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Tabele autonomiczne muszą implementować logikę `Fill` w tabelach autonomicznych, dzięki czemu można wypełniać je danymi. Aby uzyskać informacje na temat wypełniania tabel danych autonomicznych, zobacz [zapełnianie zestawu danych z elementu DataAdapter](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
