---
title: Wstawianie nowych rekordów do bazy danych | Microsoft Docs
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651559"
---
# <a name="insert-new-records-into-a-database"></a>Wstawianie nowych rekordów do bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wstawić nowe rekordy do bazy danych, można użyć metody `TableAdapter.Update` lub jednej z metod DBDirect TableAdapter (w przypadku metody `TableAdapter.Insert`).

 Jeśli aplikacja nie używa TableAdapters, można użyć obiektów poleceń (na przykład <xref:System.Data.SqlClient.SqlCommand>) do wstawienia nowych rekordów w bazie danych.

 Jeśli Twoja aplikacja korzysta z zestawów danych do przechowywania, użyj metody `TableAdapter.Update`. Metoda `Update` wysyła wszystkie zmiany (aktualizacje, wstawienia i usunięcia) do bazy danych programu.

 Jeśli aplikacja korzysta z obiektów do przechowywania danych lub jeśli chcesz mieć większą kontrolę nad tworzeniem nowych rekordów w bazie danych, użyj metody `TableAdapter.Insert`.

 Jeśli TableAdapter nie ma metody `Insert`, oznacza to, że TableAdapter jest skonfigurowany do korzystania z procedur składowanych lub jej Właściwość `GenerateDBDirectMethods` jest ustawiona na `false`. Spróbuj ustawić właściwość `GenerateDBDirectMethods` TableAdapter na `true` z Projektant obiektów Dataset, a następnie Zapisz zestaw danych. Spowoduje to ponowne wygenerowanie TableAdapter. Jeśli TableAdapter nadal nie ma metody `Insert`, tabela prawdopodobnie nie zawiera wystarczającej ilości informacji o schemacie, aby rozróżnić poszczególne wiersze (na przykład w tabeli może nie być ustawiony klucz podstawowy).

## <a name="insert-new-records-by-using-tableadapters"></a>Wstawianie nowych rekordów przy użyciu TableAdapters
 TableAdapters umożliwiają różne sposoby wstawiania nowych rekordów do bazy danych, w zależności od wymagań aplikacji.

 Jeśli aplikacja korzysta z zestawów danych w celu przechowywania dane, można po prostu dodać nowe rekordy do żądanego <xref:System.Data.DataTable> w zestawie danych, a następnie wywołać metodę `TableAdapter.Update`. Metoda `TableAdapter.Update` wysyła wszystkie zmiany w <xref:System.Data.DataTable> do bazy danych (w tym zmodyfikowane i usunięte rekordy).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Aby wstawić nowe rekordy do bazy danych za pomocą metody TableAdapter. Update

1. Dodaj nowe rekordy do żądanego <xref:System.Data.DataTable>, tworząc nowe <xref:System.Data.DataRow> i dodając je do kolekcji <xref:System.Data.DataTable.Rows%2A>. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Dodawanie wierszy do tabeli DataTable](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Po dodaniu nowych wierszy do <xref:System.Data.DataTable> Wywołaj metodę `TableAdapter.Update`. Ilość danych do zaktualizowania można kontrolować, przekazując cały <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, tablicę <xref:System.Data.DataRow>s lub jeden <xref:System.Data.DataRow>.

    Poniższy kod pokazuje, jak dodać nowy rekord do <xref:System.Data.DataTable>, a następnie wywołać metodę `TableAdapter.Update`, aby zapisać nowy wiersz w bazie danych. (W tym przykładzie używa się tabeli `Region` w bazie danych Northwind).

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Jeśli aplikacja używa obiektów do przechowywania danych, można użyć metody `TableAdapter.Insert`, aby utworzyć nowe wiersze bezpośrednio w bazie danych. Metoda `Insert` akceptuje poszczególne wartości dla każdej kolumny jako parametry. Wywołanie metody powoduje wstawienie nowego rekordu do bazy danych z wartościami parametrów przekazaną.

   Poniższa procedura używa tabeli `Region` w bazie danych Northwind jako przykładu.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Aby wstawić nowe rekordy do bazy danych za pomocą metody TableAdapter. Insert

- Wywołaj metodę `Insert` TableAdapter, przekazując wartości dla każdej kolumny jako parametry.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Wstawianie nowych rekordów przy użyciu obiektów poleceń
 W poniższym przykładzie są wstawiane nowe rekordy bezpośrednio do bazy danych przy użyciu obiektów poleceń.

 Poniższa procedura używa tabeli `Region` w bazie danych Northwind jako przykładu.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Aby wstawić nowe rekordy do bazy danych za pomocą obiektów poleceń

- Utwórz nowy obiekt polecenia, a następnie ustaw jego właściwości `Connection`, `CommandType` i `CommandText`.

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework
 Musisz mieć dostęp do bazy danych, z którą próbujesz nawiązać połączenie, oraz uprawnienia do wykonywania operacji wstawiania do odpowiedniej tabeli.

## <a name="see-also"></a>Zobacz też
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
