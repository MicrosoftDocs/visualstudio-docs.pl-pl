---
title: Aktualizowanie danych za pomocą adaptera TableAdapter | Dokumentacja firmy Microsoft
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 987e9166a9237fd1d195243f0156285338b8572a
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647199"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualizowanie danych za pomocą adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Po ukończeniu zmodyfikowane i sprawdzania poprawności danych w zestawie danych, może wysyłać zaktualizowane dane do wywoływania databaseby `Update` metody TableAdapter. `Update` Metoda aktualizuje jednej tabeli danych i uruchamia odpowiednie polecenie (INSERT, UPDATE lub DELETE), na podstawie <xref:System.Data.DataRow.RowState%2A> każdego wiersza danych w tabeli. Gdy zestaw danych zawiera tabele powiązane relacjami, program Visual Studio generuje klasę TableAdapterManager, która służy do aktualizacji. Klasa TableAdapterManager gwarantuje, że aktualizacje zostały wprowadzone w odpowiedniej kolejności, na podstawie ograniczeń klucza obcego, które są zdefiniowane w bazie danych. Korzystając z formantów powiązanych z danymi, architektura wiązania z danymi tworzy zmienną składową klasy TableAdapterManager, o nazwie tableAdapterManager. Aby uzyskać więcej informacji, zobacz [hierarchiczna aktualizacja — Przegląd](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Podczas próby aktualizacji źródła danych przy użyciu zawartości zestawu danych można uzyskać błędów. Aby uniknąć błędów, zaleca się thatyou umieść kod, który wywołuje karty `Update` metody w ramach `try` / `catch` bloku.  
  
 Dokładna procedura aktualizowanie źródła danych mogą się różnić w zależności od potrzeb biznesowych, ale obejmuje następujące kroki:  
  
1.  Wywołaj karty `Update` method in Class metoda `try` / `catch` bloku.  
  
2.  Jeśli wystąpił wyjątek, zlokalizuj wiersz danych, które spowodowały błąd. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie wierszy zawierających błędy](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Uzgodnij problem w danych wiersza (programowo, jeżeli jest to możliwe, lub poprzez przedstawienie nieprawidłowy wiersz użytkownikowi modyfikowanie), a następnie ponów próbę aktualizacji (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="savedata-to-a-database"></a>SaveData do bazy danych  
 Wywołaj `Update` metody TableAdapter. Przekaż nazwę tabeli danych, który zawiera wartości, które mają być zapisane w bazie danych.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Aby zaktualizować bazę danych za pomocą TableAdapter  
  
-   Ujmij TableAdapter`Update` method in Class metoda `try` / `catch` bloku. Poniższy przykład pokazuje, jak aktualizować zawartość `Customers` tabelę `NorthwindDataSet` z poziomu `try` / `catch` bloku.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
