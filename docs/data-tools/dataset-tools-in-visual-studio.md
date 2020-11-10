---
title: Narzędzia do obsługi zestawów danych
description: Przejrzyj narzędzia zestawu danych dostępne w programie Visual Studio. Przeczytaj informacje o przepływie pracy zestawu danych, zestawach danych i architekturze N-warstwowej oraz zestawy danych i XML.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b0ccb15d65f021099bb48c26dbdb7c03122049a7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436488"
---
# <a name="dataset-tools-in-visual-studio"></a>Narzędzia zestawów danych w programie Visual Studio

> [!NOTE]
> Zestawy danych i powiązane klasy są starszymi technologiami platformy .NET od wczesnych 2000, które umożliwiają aplikacjom współpracują z danymi w pamięci, gdy aplikacje są rozłączone z bazą danych. Są one szczególnie przydatne w przypadku aplikacji, które umożliwiają użytkownikom modyfikowanie danych i utrwalanie zmian z powrotem w bazie danych. Mimo że zestawy danych okazały się bardzo pomyślnymi technologiami, zalecamy, aby nowe aplikacje .NET używały Entity Framework. Entity Framework zapewnia bardziej naturalny sposób pracy z danymi tabelarycznymi jako modeli obiektów i ma prostszy interfejs programowania.

`DataSet`Obiekt jest obiektem znajdującym się w pamięci, który jest zasadniczo bazą danych. Zawiera `DataTable` obiekty, `DataColumn` i, `DataRow` w których można przechowywać i modyfikować dane z co najmniej jednej bazy danych bez konieczności konserwowania otwartego połączenia. Zestaw danych przechowuje informacje o zmianach w jego danych, dlatego aktualizacje mogą być śledzone i wysyłane z powrotem do bazy danych, gdy aplikacja zostanie ponownie nawiązane.

Zestawy danych i powiązane klasy są zdefiniowane w <xref:System.Data?displayProperty=fullName> przestrzeni nazw w interfejsie API platformy .NET. Zestawy danych można tworzyć i modyfikować dynamicznie w kodzie za pomocą ADO.NET. W dokumentacji w tej sekcji przedstawiono sposób pracy z zestawami danych przy użyciu projektantów programu Visual Studio. Zestawy danych tworzone za pomocą projektantów używają obiektów **TableAdapter** do współpracy z bazą danych. Zestawy danych, które są tworzone programowo, używają obiektów **DataAdapter** . Aby uzyskać informacje na temat programistycznego tworzenia zestawów danych, zobacz [DataAdapters i Datareads](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Jeśli aplikacja wymaga tylko odczytania danych z bazy danych, a nie wykonywania aktualizacji, dodania lub usunięcia, można zazwyczaj uzyskać lepszą wydajność przy użyciu `DataReader` obiektu do pobierania danych do `List` obiektu ogólnego lub innego obiektu kolekcji. Jeśli dane są wyświetlane, można powiązać interfejs użytkownika z kolekcją.

## <a name="dataset-workflow"></a>Przepływ pracy zestawu danych

Program Visual Studio udostępnia narzędzia upraszczające pracę z zestawami danych. Podstawowy kompleksowy przepływ pracy to:

- Użyj [okna źródła danych](add-new-data-sources.md#data-sources-window) , aby utworzyć nowy zestaw danych z co najmniej jednego źródła danych. Użyj **Projektant obiektów DataSet** , aby skonfigurować zestaw danych i ustawić jego właściwości. Na przykład należy określić, które tabele ze źródła danych mają zostać dołączone oraz które kolumny z każdej tabeli. Wybierz uważnie, aby zachować ilość pamięci wymaganej przez zestaw danych. Aby uzyskać więcej informacji, zobacz [Tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Określ relacje między tabelami, aby klucze obce były prawidłowo obsługiwane. Aby uzyskać więcej informacji, zobacz [Wypełnij zestawy danych za pomocą TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Użyj **Kreatora konfiguracji TableAdapter** , aby określić zapytanie lub procedurę przechowywaną, która wypełnia zestaw danych, oraz operacje bazy danych (Aktualizuj, Usuń itd.), które mają zostać wdrożone. Więcej informacji można znaleźć w następujących tematach:

  - [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Edytowanie danych w zestawach danych](../data-tools/edit-data-in-datasets.md)

  - [Weryfikowanie danych w zestawach danych](../data-tools/validate-data-in-datasets.md)

  - [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)

- Wykonywanie zapytań i wyszukiwanie danych w zestawie danych. Aby uzyskać więcej informacji, zobacz [zestawy danych zapytań](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] włącza obsługę [LINQ (opartego na języku Query)](/dotnet/csharp/linq/) za pośrednictwem danych w <xref:System.Data.DataSet> obiekcie. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Użyj okna **źródła danych** , aby powiązać kontrolki interfejsu użytkownika z zestawem danych lub jego indywidualnymi kolumnami, a także określić, które kolumny mają być edytowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Zestawy danych i architektura N-warstwowa

Aby uzyskać informacje o zestawach danych w aplikacjach N-warstwowych, zobacz [Work with datasetss in aplikacje n-warstwowe](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Zestawy danych i XML

Aby uzyskać informacje na temat konwertowania zestawów danych do i z formatu XML, zobacz [Odczytaj dane XML do zestawu danych](../data-tools/read-xml-data-into-a-dataset.md) i [Zapisz zestaw danych jako XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Zobacz też

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
