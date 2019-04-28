---
title: Wstawianie nowych rekordów do bazy danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a3fb276b3efb0d437d66d3e38c9e55b45b43e9c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566345"
---
# <a name="insert-new-records-into-a-database"></a>Wstawianie nowych rekordów do bazy danych

Wstawianie nowych rekordów do bazy danych, umożliwia `TableAdapter.Update` metody lub jednego z TableAdapter dbdirect — metody (w szczególności `TableAdapter.Insert` metody). Aby uzyskać więcej informacji, zobacz [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Jeśli aplikacja nie używają adapterów tabel, możesz użyć polecenia obiektów (na przykład <xref:System.Data.SqlClient.SqlCommand>) do wstawianie nowych rekordów w bazie danych.

Jeśli aplikacja używa zestawów danych do przechowywania danych, użyj `TableAdapter.Update` metody. `Update` Metoda wysyła wszystkie zmiany (aktualizacji, wstawiania i usuwania) w bazie danych.

Jeśli aplikacja używa obiektów do przechowywania danych lub bardziej precyzyjną kontrolę nad tworzenia nowych rekordów w bazie danych, należy użyć `TableAdapter.Insert` metody.

Jeśli Twoje TableAdapter nie ma `Insert` metody, oznacza to, że albo Obiekt TableAdapter jest skonfigurowany do używania procedur składowanych lub jego `GenerateDBDirectMethods` właściwość jest ustawiona na `false`. Spróbuj ustawić TableAdapter `GenerateDBDirectMethods` właściwości `true` z poziomu **Projektanta obiektów Dataset**, a następnie Zapisz zestaw danych. Spowoduje to ponowne wygenerowanie TableAdapter. Jeśli w metodzie TableAdapter nie ma `Insert` metoda, tabeli prawdopodobnie nie dostarcza wystarczających informacji o schemacie rozróżnienie między poszczególnymi wierszami (na przykład może istnieć nie podstawowego zestawu kluczy w tabeli).

## <a name="insert-new-records-by-using-tableadapters"></a>Wstawianie nowych rekordów za pomocą adapterów TableAdapter

TableAdapters zapewniają różne sposoby wstawianie nowych rekordów do bazy danych, w zależności od wymagań aplikacji.

Jeśli aplikacja używa zestawów danych do przechowywania danych, można po prostu Dodaj nowe rekordy na żądaną <xref:System.Data.DataTable> w zestawie danych, a następnie wywołania `TableAdapter.Update` metody. `TableAdapter.Update` Metoda wysyła wszystkie zmiany <xref:System.Data.DataTable> do bazy danych (w tym zmodyfikowane i usuniętych rekordów).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Wstawianie nowych rekordów do bazy danych za pomocą TableAdapter.Update — metoda

1. Dodawanie nowych rekordów do żądaną <xref:System.Data.DataTable> przez utworzenie nowego <xref:System.Data.DataRow> i dodanie go do <xref:System.Data.DataTable.Rows%2A> kolekcji.

2. Po dodaniu nowych wierszy do <xref:System.Data.DataTable>, wywołaj `TableAdapter.Update` metody. Możesz kontrolować ilość danych, które można zaktualizować przez przekazanie albo cały <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, tablicę <xref:System.Data.DataRow>s lub pojedynczej <xref:System.Data.DataRow>.

   Poniższy kod przedstawia sposób dodawania nowego rekordu do <xref:System.Data.DataTable> , a następnie wywołać `TableAdapter.Update` metodę, aby zapisać nowy wiersz w bazie danych. (W tym przykładzie użyto `Region` tabeli w bazie danych Northwind.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Wstawianie nowych rekordów do bazy danych za pomocą TableAdapter.INSERT — metoda

Jeśli aplikacja używa obiektów do przechowywania danych, możesz użyć `TableAdapter.Insert` metodę w celu utworzenia nowych wierszy bezpośrednio w bazie danych. `Insert` Metoda przyjmuje jako parametry poszczególne wartości dla każdej kolumny. Wywołanie metody Wstawia nowy rekord do bazy danych przy użyciu wartości parametrów przekazanych.

- Wywołaj TableAdapter `Insert` jest metoda wartości dla każdej kolumny jako parametry.

Poniższa procedura demonstruje użycie `TableAdapter.Insert` metodę, aby wstawić wiersze. W tym przykładzie wstawia dane do `Region` tabeli w bazie danych Northwind.

> [!NOTE]
> Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz użyć.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Wstawianie nowych rekordów przy użyciu polecenia obiektów

Za wstawianie nowych rekordów bezpośrednio do bazy danych przy użyciu polecenia obiektów.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Aby wstawianie nowych rekordów do bazy danych przy użyciu polecenia obiektów

- Utwórz nowy obiekt polecenia, a następnie ustaw jego `Connection`, `CommandType`, i `CommandText` właściwości.

W poniższym przykładzie pokazano Wstawianie rekordów do bazy danych za pomocą obiektu polecenia. Wstawia dane do `Region` tabeli w bazie danych Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework

Musi mieć dostęp do bazy danych, z którym próbujesz nawiązać połączenie, a także uprawnienia do wykonywania operacji wstawiania do żądanej tabeli.

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)