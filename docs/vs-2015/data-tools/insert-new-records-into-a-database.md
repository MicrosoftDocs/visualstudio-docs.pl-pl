---
title: Wstawianie nowych rekordów do bazy danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2e4dbae766efbcf56fb421d62239ae3325cc1423
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648247"
---
# <a name="insert-new-records-into-a-database"></a>Wstawianie nowych rekordów do bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Wstawianie nowych rekordów do bazy danych, umożliwia `TableAdapter.Update` metody lub jednego z TableAdapter dbdirect — metody (w szczególności `TableAdapter.Insert` metody).
  
 Jeśli aplikacja nie używają adapterów tabel, możesz użyć polecenia obiektów (na przykład <xref:System.Data.SqlClient.SqlCommand>) do wstawianie nowych rekordów w bazie danych.  
  
 Jeśli aplikacja używa zestawów danych do przechowywania danych, użyj `TableAdapter.Update` metody. `Update` Metoda wysyła wszystkie zmiany (aktualizacji, wstawiania i usuwania) w bazie danych.  
  
 Jeśli aplikacja używa obiektów do przechowywania danych lub bardziej precyzyjną kontrolę nad tworzenia nowych rekordów w bazie danych, należy użyć `TableAdapter.Insert` metody.  
  
 Jeśli Twoje TableAdapter nie ma `Insert` metody, oznacza to, że albo Obiekt TableAdapter jest skonfigurowany do używania procedur składowanych lub jego `GenerateDBDirectMethods` właściwość jest ustawiona na `false`. Spróbuj ustawić TableAdapter `GenerateDBDirectMethods` właściwość `true` z w Projektancie obiektów Dataset, a następnie Zapisz zestaw danych. Spowoduje to ponowne wygenerowanie TableAdapter. Jeśli w metodzie TableAdapter nie ma `Insert` metody, a następnie tabeli prawdopodobnie nie zapewnia wystarczającą ilość informacji o schemacie rozróżnienie między poszczególnymi wierszami (na przykład może istnieć nie podstawowego zestawu kluczy w tabeli).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Wstawianie nowych rekordów za pomocą adapterów TableAdapter  
 TableAdapters zapewniają różne sposoby wstawianie nowych rekordów do bazy danych, w zależności od wymagań aplikacji.  
  
 Jeśli aplikacja używa zestawów danych do przechowywania danych, a następnie można po prostu Dodaj nowe rekordy na żądaną <xref:System.Data.DataTable> w zestawie danych, a następnie wywołania `TableAdapter.Update` metody. `TableAdapter.Update` Metoda wysyła wszystkie zmiany <xref:System.Data.DataTable> do bazy danych (w tym zmodyfikowane i usuniętych rekordów).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Wstawianie nowych rekordów do bazy danych za pomocą TableAdapter.Update — metoda  
  
1. Dodawanie nowych rekordów do żądaną <xref:System.Data.DataTable> przez utworzenie nowego <xref:System.Data.DataRow> i dodanie go do <xref:System.Data.DataTable.Rows%2A> kolekcji. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie wierszy do DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).  
  
2. Po dodaniu nowych wierszy do <xref:System.Data.DataTable>, wywołaj `TableAdapter.Update` metody. Możesz kontrolować ilość danych, które można zaktualizować przez przekazanie albo cały <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, tablicę <xref:System.Data.DataRow>s lub pojedynczej <xref:System.Data.DataRow>.  
  
    Poniższy kod przedstawia sposób dodawania nowego rekordu do <xref:System.Data.DataTable> , a następnie wywołać `TableAdapter.Update` metodę, aby zapisać nowy wiersz w bazie danych. (W tym przykładzie użyto `Region` tabeli w bazie danych Northwind.)  
  
    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]  
  
   Jeśli aplikacja używa obiektów do przechowywania danych, możesz użyć `TableAdapter.Insert` metodę w celu utworzenia nowych wierszy bezpośrednio w bazie danych. `Insert` Metoda przyjmuje jako parametry poszczególne wartości dla każdej kolumny. Wywołanie metody Wstawia nowy rekord do bazy danych przy użyciu wartości parametrów przekazanych.  
  
   W poniższej procedurze użyto `Region` tabeli w bazie danych Northwind jako przykład.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Wstawianie nowych rekordów do bazy danych za pomocą TableAdapter.INSERT — metoda  
  
-   Wywołaj TableAdapter `Insert` jest metoda wartości dla każdej kolumny jako parametry.  
  
    > [!NOTE]
    >  Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz użyć.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Wstawianie nowych rekordów przy użyciu polecenia obiektów  
 Poniższy przykład wstawia nowe rekordy bezpośrednio do bazy danych przy użyciu polecenia obiektów.
  
 W poniższej procedurze użyto `Region` tabeli w bazie danych Northwind jako przykład.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Aby wstawianie nowych rekordów do bazy danych przy użyciu polecenia obiektów  
  
-   Utwórz nowy obiekt polecenia, a następnie ustaw jego `Connection`, `CommandType`, i `CommandText` właściwości.  
  
     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Musi mieć dostęp do bazy danych, z którym próbujesz nawiązać połączenie, a także uprawnienia do wykonywania operacji wstawiania do żądanej tabeli.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
