---
title: Aktualizowanie danych za pomocą adaptera TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 546ca45ed48f9fc247bd5706005153f41cf206e5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926765"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualizowanie danych za pomocą adaptera TableAdapter

Po danych w zestawie danych, został zmodyfikowany i zweryfikowany, zaktualizowane dane może wysyłać do bazy danych, wywołując `Update` metody [TableAdapter](../data-tools/create-and-configure-tableadapters.md). `Update` Metoda aktualizuje jednej tabeli danych i uruchamia odpowiednie polecenie (INSERT, UPDATE lub DELETE), na podstawie <xref:System.Data.DataRow.RowState%2A> każdego wiersza danych w tabeli. Gdy zestaw danych zawiera tabele powiązane relacjami, program Visual Studio generuje klasę TableAdapterManager, która służy do aktualizacji. Klasa TableAdapterManager gwarantuje, że aktualizacje zostały wprowadzone w odpowiedniej kolejności, na podstawie ograniczeń klucza obcego, które są zdefiniowane w bazie danych. Korzystając z formantów powiązanych z danymi, architektura wiązania z danymi tworzy zmienną składową klasy TableAdapterManager, o nazwie tableAdapterManager.

> [!NOTE]
> Podczas próby aktualizacji źródła danych przy użyciu zawartości zestawu danych można uzyskać błędów. Aby uniknąć błędów, zaleca się umieścić kod, który wywołuje karty `Update` metody w ramach `try` / `catch` bloku.

 Dokładna procedura aktualizowanie źródła danych mogą się różnić w zależności od potrzeb biznesowych, ale obejmuje następujące kroki:

1.  Wywołaj karty `Update` method in Class metoda `try` / `catch` bloku.

2.  Jeśli wystąpił wyjątek, zlokalizuj wiersz danych, które spowodowały błąd.

3.  Uzgodnij problem w danych wiersza (programowo, jeżeli jest to możliwe, lub poprzez przedstawienie nieprawidłowy wiersz użytkownikowi modyfikowanie), a następnie ponów próbę aktualizacji (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Zapisywanie danych w bazie danych

Wywołaj `Update` metody TableAdapter. Przekaż nazwę tabeli danych, który zawiera wartości, które mają być zapisane w bazie danych.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Aby zaktualizować bazę danych za pomocą TableAdapter

-   Ujmij TableAdapter`Update` method in Class metoda `try` / `catch` bloku. Poniższy przykład pokazuje, jak aktualizować zawartość `Customers` tabelę `NorthwindDataSet` z poziomu `try` / `catch` bloku.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)