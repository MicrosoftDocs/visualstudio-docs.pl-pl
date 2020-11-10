---
title: Wstawianie nowych rekordów do bazy danych
description: Wstaw nowe rekordy do bazy danych przy użyciu metody TableAdapter. Update, jednej z metod DBDirect TableAdapter lub obiektów poleceń.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3586cf45e152cd8a0149140556916b11544a00bb
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436279"
---
# <a name="insert-new-records-into-a-database"></a>Wstawianie nowych rekordów do bazy danych

Aby wstawić nowe rekordy do bazy danych, można użyć `TableAdapter.Update` metody lub jednej z metod DBDirect TableAdapter ( `TableAdapter.Insert` Metoda). Aby uzyskać więcej informacji, zobacz [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Jeśli aplikacja nie używa TableAdapters, można użyć obiektów poleceń (na przykład  <xref:System.Data.SqlClient.SqlCommand> ) do wstawienia nowych rekordów w bazie danych.

Jeśli Twoja aplikacja korzysta z zestawów danych do przechowywania, użyj `TableAdapter.Update` metody. `Update`Metoda wysyła wszystkie zmiany (aktualizacje, wstawienia i usunięcia) do bazy danych programu.

Jeśli aplikacja korzysta z obiektów do przechowywania danych lub jeśli chcesz mieć większą kontrolę nad tworzeniem nowych rekordów w bazie danych, użyj `TableAdapter.Insert` metody.

Jeśli TableAdapter nie ma `Insert` metody, oznacza to, że TableAdapter jest skonfigurowany do korzystania z procedur składowanych lub jej `GenerateDBDirectMethods` Właściwość jest ustawiona na `false` . Spróbuj ustawić `GenerateDBDirectMethods` Właściwość TableAdapter na `true` wartość z w **Projektant obiektów DataSet** , a następnie Zapisz zestaw danych. Spowoduje to ponowne wygenerowanie TableAdapter. Jeśli TableAdapter nadal nie ma `Insert` metody, tabela prawdopodobnie nie zawiera wystarczającej ilości informacji o schemacie do rozróżnienia między pojedynczymi wierszami (na przykład w tabeli może nie być ustawiony klucz podstawowy).

## <a name="insert-new-records-by-using-tableadapters"></a>Wstawianie nowych rekordów przy użyciu TableAdapters

TableAdapters umożliwiają różne sposoby wstawiania nowych rekordów do bazy danych, w zależności od wymagań aplikacji.

Jeśli aplikacja korzysta z zestawów danych w celu przechowywania, można po prostu dodać nowe rekordy do żądanego <xref:System.Data.DataTable> zestawu danych, a następnie wywołać `TableAdapter.Update` metodę. `TableAdapter.Update`Metoda wysyła zmiany <xref:System.Data.DataTable> do bazy danych programu (w tym zmodyfikowane i usunięte rekordy).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Aby wstawić nowe rekordy do bazy danych za pomocą metody TableAdapter. Update

1. Dodaj nowe rekordy do żądanego, <xref:System.Data.DataTable> tworząc nowe <xref:System.Data.DataRow> i dodając je do <xref:System.Data.DataTable.Rows%2A> kolekcji.

2. Po dodaniu nowych wierszy do <xref:System.Data.DataTable> , wywołaj `TableAdapter.Update` metodę. Ilość danych do zaktualizowania można kontrolować, przekazując ją w całości <xref:System.Data.DataSet> , a <xref:System.Data.DataTable> , tablicę <xref:System.Data.DataRow> s lub pojedynczo <xref:System.Data.DataRow> .

   Poniższy kod pokazuje, jak dodać nowy rekord do <xref:System.Data.DataTable> a następnie wywołać `TableAdapter.Update` metodę, aby zapisać nowy wiersz w bazie danych. (W tym przykładzie używa się `Region` tabeli w bazie danych Northwind).

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Aby wstawić nowe rekordy do bazy danych za pomocą metody TableAdapter. Insert

Jeśli aplikacja używa obiektów do przechowywania danych, można użyć `TableAdapter.Insert` metody, aby utworzyć nowe wiersze bezpośrednio w bazie danych. `Insert`Metoda akceptuje poszczególne wartości dla każdej kolumny jako parametry. Wywołanie metody powoduje wstawienie nowego rekordu do bazy danych z wartościami parametrów przekazaną.

- Wywołaj metodę TableAdapter `Insert` , przekazując wartości dla każdej kolumny jako parametry.

Poniższa procedura ilustruje użycie `TableAdapter.Insert` metody do wstawiania wierszy. Ten przykład wstawia dane do `Region` tabeli w bazie danych Northwind.

> [!NOTE]
> Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Wstawianie nowych rekordów przy użyciu obiektów poleceń

Nowe rekordy można wstawiać bezpośrednio do bazy danych przy użyciu obiektów poleceń.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Aby wstawić nowe rekordy do bazy danych za pomocą obiektów poleceń

- Utwórz nowy obiekt polecenia, a następnie ustaw jego `Connection` właściwości, `CommandType` i `CommandText` .

Poniższy przykład ilustruje wstawianie rekordów do bazy danych przy użyciu obiektu polecenia. Wstawia dane do `Region` tabeli w bazie danych Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Musisz mieć dostęp do bazy danych, z którą próbujesz nawiązać połączenie, oraz uprawnienia do wykonywania operacji wstawiania do odpowiedniej tabeli.

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
