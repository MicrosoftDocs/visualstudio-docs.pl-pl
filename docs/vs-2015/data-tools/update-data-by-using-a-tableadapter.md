---
title: Aktualizowanie danych za pomocą TableAdapter | Microsoft Docs
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
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602334"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualizowanie danych za pomocą adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zmodyfikowaniu i sprawdzeniu poprawności danych w zestawie danych można wysłać zaktualizowane dane z powrotem do databaseby wywołującego `Update` metodę TableAdapter. `Update`Metoda aktualizuje pojedynczą tabelę danych i uruchamia poprawne polecenie (INSERT, Update lub Delete) na podstawie <xref:System.Data.DataRow.RowState%2A> każdego wiersza danych w tabeli. Gdy zestaw danych zawiera powiązane tabele, program Visual Studio generuje klasę TableAdapterManager, która jest używana do wykonywania aktualizacji. Klasa TableAdapterManager gwarantuje, że aktualizacje są wprowadzane w odpowiedniej kolejności na podstawie ograniczeń klucza obcego, które są zdefiniowane w bazie danych. W przypadku korzystania z kontrolek powiązanych z danymi architektura wiązania danych tworzy zmienną członkowską klasy TableAdapterManager o nazwie tableAdapterManager. Aby uzyskać więcej informacji, zobacz [Omówienie hierarchicznej aktualizacji](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).

> [!NOTE]
> Podczas próby zaktualizowania źródła danych za pomocą zawartości zestawu danych można uzyskać błędy. Aby uniknąć błędów, zalecamy thatyou umieścić kod, który wywołuje metodę adaptera `Update` w `try` / `catch` bloku.

 Dokładna procedura aktualizowania źródła danych może się różnić w zależności od potrzeb firmy, ale obejmuje następujące kroki:

1. Wywołaj metodę adaptera `Update` w `try` / `catch` bloku.

2. W przypadku przechwyconego wyjątku Znajdź wiersz danych, który spowodował błąd. Aby uzyskać więcej informacji, zobacz [How to: Lokalizuj wiersze z błędami](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).

3. Uzgodnij problem z wierszem danych (programowo, jeśli możesz lub przez przedstawienie nieprawidłowego wiersza użytkownikowi do modyfikacji), a następnie spróbuj ponownie wykonać aktualizację ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="savedata-to-a-database"></a>SaveData do bazy danych
 Wywołaj `Update` metodę elementu TableAdapter. Przekaż nazwę tabeli danych zawierającą wartości, które mają być zapisywane w bazie danych.

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Aby zaktualizować bazę danych za pomocą TableAdapter

- Ujmij `Update` metodę TableAdapter w `try` / `catch` bloku. Poniższy przykład pokazuje, jak zaktualizować zawartość `Customers` tabeli `NorthwindDataSet` z wewnątrz `try` / `catch` bloku.

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>Zobacz też
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
