---
title: Zapisywanie danych z obiektu do bazy danych | Dokumentacja firmy Microsoft
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c079d3f85dbab87e30edb059c76202dd727f715c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425061"
---
# <a name="save-data-from-an-object-to-a-database"></a>Zapisywanie danych z obiektu w bazie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zapisać danych w obiektach do bazy danych przez przekazanie wartości z obiektu do jednej z TableAdapter dbdirect — metody (na przykład `TableAdapter.Insert`).
  
 Aby zapisać dane z kolekcji obiektów, w pętli poprzez kolekcji obiektów (na przykład pętli for dalej) i wysłać wartości dla każdego obiektu do bazy danych przy użyciu jednej z TableAdapter dbdirect — metody.  
  
 Domyślnie dbdirect — metody są tworzone na obiekt TableAdapter, który można uruchomić bezpośrednio w bazie danych. Te metody może być wywoływana bezpośrednio i nie wymagają <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> obiektów uzgadniają zmiany w celu wysyłania aktualizacji do bazy danych.  
  
> [!NOTE]
> Podczas konfiguracji TableAdapter główne zapytanie musi dostarczać wystarczających informacji dla dbdirect — metody ma zostać utworzony. Na przykład jeśli TableAdapter jest skonfigurowany do zapytania o dane z tabeli, która nie ma kolumny klucza podstawowego zdefiniowane, go nie generuje dbdirect — metody.  
  
|TableAdapter dbdirect — metody|Opis|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Dodanie nowych rekordów do bazy danych i umożliwia przekazywanie wartości poszczególnych kolumn jako parametry metody.|  
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. `Update` Metoda przyjmuje wartości oryginalnego i nowych kolumn jako parametry metody. Oryginalne wartości są używane do lokalizowania oryginalnego rekordu, a nowe wartości są używane na zaktualizowanie rekordu.<br /><br /> `TableAdapter.Update` Metoda umożliwia również uzgadniają zmiany w zestawie danych w bazie danych, wykonując <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, lub tablicę <xref:System.Data.DataRow>określane jako parametry metody.|  
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych oparte na oryginalnych wartości kolumny przekazanych jako parametry metody.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>Aby zapisać nowe rekordy z obiektu do bazy danych  
  
- Tworzenie rekordów przez przekazanie wartości do `TableAdapter.Insert` metody.  
  
     Poniższy przykład tworzy nowy rekord klienta `Customers` tabeli przez przekazanie wartości w `currentCustomer` obiekt `TableAdapter.Insert` metody.  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aby zaktualizować istniejące rekordy z obiektu do bazy danych  
  
- Modyfikowanie rekordów, wywołując `TableAdapter.Update` metody, przekazując nowe wartości w celu zaktualizowania rekordu, a w oryginalnych wartości, aby zlokalizować rekordu.  
  
    > [!NOTE]
    > Trzeba zachować oryginalne wartości, aby można było przekazać je do obiektu `Update` metody. W tym przykładzie użyto właściwości `orig` prefiks do przechowywania oryginalnych wartości.  
  
     Poniższy przykład aktualizuje istniejący rekord w `Customers` tabeli przez przekazanie wartości nowymi i oryginalnymi `Customer` obiekt `TableAdapter.Update` metody.  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>Aby usunąć istniejące rekordy z bazy danych  
  
- Usuń rekordy przez wywołanie metody `TableAdapter.Delete` metody i przekazywanie w oryginalnej wartości do wyszukania w rekordzie.  
  
    > [!NOTE]
    > Trzeba zachować oryginalne wartości, aby można było przekazać je do obiektu `Delete` metody. W tym przykładzie użyto właściwości `orig` prefiks do przechowywania oryginalnych wartości.  
  
     Poniższy przykład usuwa rekord na podstawie `Customers` tabeli, przekazując oryginalnych wartości w `Customer` obiekt `TableAdapter.Delete` metody.  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Musi mieć uprawnienia do wykonania wybranej INSERT, UPDATE lub DELETE w tabeli w bazie danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
