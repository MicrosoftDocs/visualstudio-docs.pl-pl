---
title: Aktualizowanie danych za pomocą adaptera TableAdapter
description: Aktualizowanie danych w zestawie danych. Wyślij dane z powrotem do bazy danych, wywołując metodę Update metody TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f3054c5c74c8844f780c3562327353fca164f1f4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215646"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualizowanie danych za pomocą adaptera TableAdapter

Po zmodyfikowaniu i sprawdzeniu poprawności danych w zestawie danych można wysłać zaktualizowane dane z powrotem do bazy danych przez wywołanie `Update` metody [TableAdapter](../data-tools/create-and-configure-tableadapters.md). `Update`Metoda aktualizuje pojedynczą tabelę danych i uruchamia poprawne polecenie (INSERT, Update lub Delete) na podstawie <xref:System.Data.DataRow.RowState%2A> każdego wiersza danych w tabeli. Gdy zestaw danych zawiera powiązane tabele, program Visual Studio generuje klasę TableAdapterManager, która jest używana do wykonywania aktualizacji. Klasa TableAdapterManager gwarantuje, że aktualizacje są wprowadzane w odpowiedniej kolejności na podstawie ograniczeń klucza obcego, które są zdefiniowane w bazie danych. W przypadku korzystania z kontrolek powiązanych z danymi architektura wiązania danych tworzy zmienną członkowską klasy TableAdapterManager o nazwie tableAdapterManager.

> [!NOTE]
> Podczas próby zaktualizowania źródła danych za pomocą zawartości zestawu danych można uzyskać błędy. Aby uniknąć błędów, zalecamy umieszczenie kodu, który wywołuje metodę adaptera `Update` w `try` / `catch` bloku.

Dokładna procedura aktualizowania źródła danych może się różnić w zależności od potrzeb firmy, ale obejmuje następujące kroki:

1. Wywołaj metodę adaptera `Update` w `try` / `catch` bloku.

2. W przypadku przechwyconego wyjątku Znajdź wiersz danych, który spowodował błąd.

3. Uzgodnij problem z wierszem danych (programowo, jeśli możesz lub przez przedstawienie nieprawidłowego wiersza użytkownikowi do modyfikacji), a następnie spróbuj ponownie wykonać aktualizację ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="save-data-to-a-database"></a>Zapisywanie danych w bazie danych

Wywołaj `Update` metodę elementu TableAdapter. Przekaż nazwę tabeli danych zawierającą wartości, które mają być zapisywane w bazie danych.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Aby zaktualizować bazę danych za pomocą TableAdapter

- Ujmij `Update` metodę TableAdapter w `try` / `catch` bloku. Poniższy przykład pokazuje, jak zaktualizować zawartość `Customers` tabeli `NorthwindDataSet` z wewnątrz `try` / `catch` bloku.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet9":::

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
