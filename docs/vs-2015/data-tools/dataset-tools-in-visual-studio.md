---
title: Narzędzia do obsługi zestawów danych
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 553d4f7ca61bbc01e72e8735b0007d2f08876e71
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666510"
---
# <a name="dataset-tools-in-visual-studio"></a>Narzędzia zestawu danych w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UWAGA]
>  Zestawy danych i powiązanych klas są starszej technologii .NET, od początku 2000s, które umożliwiają aplikacjom do pracy z danymi w pamięci, gdy aplikacje są odłączone od bazy danych. Są one szczególnie przydatne w przypadku aplikacji, które umożliwiają użytkownikom modyfikowanie danych i utrwala zmiany w bazie danych. Mimo że zestawy danych okazały się być odniosła technologii, zalecane jest użycie programu Entity Framework w nowej aplikacji platformy .NET. Entity Framework zapewnia bardziej naturalny sposób pracy z danymi tabelarycznymi jako modele obiektów i ma prostsze interfejs programowania.

 Obiekt DataSet jest obiekt w pamięci, który jest zasadniczo mini bazy danych. Zawiera ona obiekty DataTable, DataColumn i DataRow, w których można przechowywać i modyfikować dane z jednego lub więcej baz danych bez konieczności utrzymywanie otwartego połączenia. Zestaw danych przechowuje informacje o zmianach wprowadzonych do jego danych, więc aktualizacje, które mogą być śledzone i wysyłane z powrotem do bazy danych, gdy aplikacja staje się zakończone.

 Zestawy danych i powiązanych klas są zdefiniowane w przestrzeni nazw System.Data w bibliotece klas programu .NET Framework. Można tworzyć i modyfikować zestawy danych dynamicznie w kodzie. Aby uzyskać więcej informacji o tym, jak to zrobić Zobacz ADO.NET. W dokumentacji w tej sekcji przedstawiono sposób pracy z zestawami danych za pomocą projektantów programu Visual Studio. Warto wiedzieć: zestawy danych, które odbywa się za pomocą projektantów za pomocą TableAdapter obiektów korzystanie z bazy danych, natomiast zestawów danych, które są wykonywane programowo za pomocą obiektów DataAdapter. Aby dowiedzieć się, jak programowe tworzenie zestawów danych, zobacz [DataAdapter i DataReaders](http://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Jeśli aplikacja musi jedynie odczytywać dane z bazy danych, a nie wykonywania aktualizacji, dodaje lub usuwa, można zwykle uzyskać lepszą wydajność przy użyciu elementu DataReader obiektu do pobrania danych do ogólnego obiekt listy lub innego obiektu kolekcji. W przypadku wyświetlania danych, użytkownik może wiązania danych interfejsu użytkownika do kolekcji.

## <a name="dataset-workflow"></a>Zestaw danych przepływu pracy
 Program Visual Studio udostępnia wiele narzędzi w celu uproszczenia pracy z zestawami danych. Podstawowy przepływ pracy end-to-end jest:

-   Użyj **źródła danych** okna, aby utworzyć nowy zestaw danych z co najmniej jedno źródło danych. Użyj **Projektanta obiektów Dataset** do konfigurowania zestawu danych i ustaw jego właściwości. Na przykład należy określić tabel ze źródła danych do uwzględnienia, a które kolumny z każdej tabeli. Wybierz dokładnie oszczędzać ilość pamięci, która wymaga zestawu danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Określ relacje między tabelami i kluczy obcych są obsługiwane poprawnie. Aby uzyskać więcej informacji, zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

-   Użyj **Kreator konfiguracji TableAdapter** określić zapytanie lub procedura składowana, który zostanie wypełniony zestawu danych i jakie operacje bazy danych (update, delete itd.) do zaimplementowania. Aby uzyskać więcej informacji zobacz następujące tematy:

    -   [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

    -   [Edytowanie danych w zestawach danych](../data-tools/edit-data-in-datasets.md)

    -   [Weryfikowanie danych w zestawach danych](../data-tools/validate-data-in-datasets.md)

    -   [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)

-   Zapytania i wyszukiwać dane w zestawie danych. Aby uzyskać więcej informacji, zobacz [zestawów danych zapytania](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] Włącza [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) nad danymi w <xref:System.Data.DataSet> obiektu. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

-   Użyj **źródeł danych** okna, aby powiązać formanty interfejsu użytkownika z zestawu danych lub jego poszczególnych kolumn i określić, które kolumny są można edytować użytkownika. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Zestawy danych i N-warstwowej architektury
 Aby uzyskać informacji na temat zestawów danych w aplikacjach N-warstwowej, zobacz [Praca z zestawami danych w aplikacjach n warstwowych](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Zestawy danych i XML
 Aby dowiedzieć się, jak konwertowanie zestawów danych do i z pliku XML, zobacz [XML odczytu danych do zestawu danych](../data-tools/read-xml-data-into-a-dataset.md) i [Zapisywanie zestawu danych jako XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
