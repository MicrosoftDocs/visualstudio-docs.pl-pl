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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aaca23e6aa81fab958fc813fa5e2331f8906a562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648313"
---
# <a name="insert-new-records-into-a-database"></a>Wstawianie nowych rekordów do bazy danych

Aby wstawić nowe rekordy do bazy danych, można użyć metody `TableAdapter.Update` lub jednej z metod DBDirect TableAdapter (w przypadku metody `TableAdapter.Insert`). Aby uzyskać więcej informacji, zobacz [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Jeśli aplikacja nie używa TableAdapters, można użyć obiektów poleceń (na przykład <xref:System.Data.SqlClient.SqlCommand>) do wstawienia nowych rekordów w bazie danych.

Jeśli Twoja aplikacja korzysta z zestawów danych do przechowywania, użyj metody `TableAdapter.Update`. Metoda `Update` wysyła wszystkie zmiany (aktualizacje, wstawienia i usunięcia) do bazy danych programu.

Jeśli aplikacja korzysta z obiektów do przechowywania danych lub jeśli chcesz mieć większą kontrolę nad tworzeniem nowych rekordów w bazie danych, użyj metody `TableAdapter.Insert`.

Jeśli TableAdapter nie ma metody `Insert`, oznacza to, że TableAdapter jest skonfigurowany do korzystania z procedur składowanych lub jej Właściwość `GenerateDBDirectMethods` jest ustawiona na `false`. Spróbuj ustawić właściwość `GenerateDBDirectMethods` TableAdapter na `true` z **Projektant obiektów DataSet**, a następnie Zapisz zestaw danych. Spowoduje to ponowne wygenerowanie TableAdapter. Jeśli TableAdapter nadal nie ma metody `Insert`, tabela prawdopodobnie nie zawiera wystarczającej ilości informacji o schemacie do rozróżnienia między pojedynczymi wierszami (na przykład w tabeli może nie być ustawiony klucz podstawowy).

## <a name="insert-new-records-by-using-tableadapters"></a>Wstawianie nowych rekordów przy użyciu TableAdapters

TableAdapters umożliwiają różne sposoby wstawiania nowych rekordów do bazy danych, w zależności od wymagań aplikacji.

Jeśli aplikacja korzysta z zestawów danych w celu przechowywania, można po prostu dodać nowe rekordy do żądanego <xref:System.Data.DataTable> w zestawie danych, a następnie wywołać metodę `TableAdapter.Update`. Metoda `TableAdapter.Update` wysyła wszystkie zmiany w <xref:System.Data.DataTable> do bazy danych (w tym zmodyfikowane i usunięte rekordy).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Aby wstawić nowe rekordy do bazy danych za pomocą metody TableAdapter. Update

1. Dodaj nowe rekordy do żądanego <xref:System.Data.DataTable>, tworząc nowe <xref:System.Data.DataRow> i dodając je do kolekcji <xref:System.Data.DataTable.Rows%2A>.

2. Po dodaniu nowych wierszy do <xref:System.Data.DataTable> Wywołaj metodę `TableAdapter.Update`. Ilość danych do zaktualizowania można kontrolować, przekazując cały <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, tablicę <xref:System.Data.DataRow>s lub jeden <xref:System.Data.DataRow>.

   Poniższy kod pokazuje, jak dodać nowy rekord do <xref:System.Data.DataTable>, a następnie wywołać metodę `TableAdapter.Update`, aby zapisać nowy wiersz w bazie danych. (W tym przykładzie używa się tabeli `Region` w bazie danych Northwind).

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Aby wstawić nowe rekordy do bazy danych za pomocą metody TableAdapter. Insert

Jeśli aplikacja używa obiektów do przechowywania danych, można użyć metody `TableAdapter.Insert`, aby utworzyć nowe wiersze bezpośrednio w bazie danych. Metoda `Insert` akceptuje poszczególne wartości dla każdej kolumny jako parametry. Wywołanie metody powoduje wstawienie nowego rekordu do bazy danych z wartościami parametrów przekazaną.

- Wywołaj metodę `Insert` TableAdapter, przekazując wartości dla każdej kolumny jako parametry.

W poniższej procedurze pokazano, jak wstawić wiersze przy użyciu metody `TableAdapter.Insert`. W tym przykładzie dane są wstawiane do tabeli `Region` w bazie danych Northwind.

> [!NOTE]
> Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Wstawianie nowych rekordów przy użyciu obiektów poleceń

Nowe rekordy można wstawiać bezpośrednio do bazy danych przy użyciu obiektów poleceń.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Aby wstawić nowe rekordy do bazy danych za pomocą obiektów poleceń

- Utwórz nowy obiekt polecenia, a następnie ustaw jego właściwości `Connection`, `CommandType` i `CommandText`.

Poniższy przykład ilustruje wstawianie rekordów do bazy danych przy użyciu obiektu polecenia. Wstawia dane do tabeli `Region` w bazie danych Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Musisz mieć dostęp do bazy danych, z którą próbujesz nawiązać połączenie, oraz uprawnienia do wykonywania operacji wstawiania do odpowiedniej tabeli.

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)