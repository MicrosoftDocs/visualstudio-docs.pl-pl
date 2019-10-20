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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b54aeb91ea873b23b1e68731e40542df04fcbd01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648123"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualizowanie danych za pomocą adaptera TableAdapter

Po zmodyfikowaniu i sprawdzeniu poprawności danych w zestawie danych można wysłać zaktualizowane dane z powrotem do bazy danych, wywołując metodę `Update` [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Metoda `Update` aktualizuje pojedynczą tabelę danych i uruchamia poprawne polecenie (INSERT, UPDATE lub DELETE) na podstawie <xref:System.Data.DataRow.RowState%2A> każdego wiersza danych w tabeli. Gdy zestaw danych zawiera powiązane tabele, program Visual Studio generuje klasę TableAdapterManager, która jest używana do wykonywania aktualizacji. Klasa TableAdapterManager gwarantuje, że aktualizacje są wprowadzane w odpowiedniej kolejności na podstawie ograniczeń klucza obcego, które są zdefiniowane w bazie danych. W przypadku korzystania z kontrolek powiązanych z danymi architektura wiązania danych tworzy zmienną członkowską klasy TableAdapterManager o nazwie tableAdapterManager.

> [!NOTE]
> Podczas próby zaktualizowania źródła danych za pomocą zawartości zestawu danych można uzyskać błędy. Aby uniknąć błędów, zalecamy umieszczenie kodu wywołującego metodę `Update` karty w bloku `try` / `catch`.

Dokładna procedura aktualizowania źródła danych może się różnić w zależności od potrzeb firmy, ale obejmuje następujące kroki:

1. Wywołaj metodę `Update` karty w bloku `try` / `catch`.

2. W przypadku przechwyconego wyjątku Znajdź wiersz danych, który spowodował błąd.

3. Uzgodnij problem z wierszem danych (programowo, jeśli możesz lub przez przedstawienie nieprawidłowego wiersza do modyfikacji użytkownika), a następnie spróbuj ponownie wykonać aktualizację (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Zapisywanie danych w bazie danych

Wywołaj metodę `Update` elementu TableAdapter. Przekaż nazwę tabeli danych zawierającą wartości, które mają być zapisywane w bazie danych.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Aby zaktualizować bazę danych za pomocą TableAdapter

- Ujmij metodę `Update` TableAdapter w bloku `try` / `catch`. Poniższy przykład pokazuje, jak zaktualizować zawartość tabeli `Customers` w `NorthwindDataSet` z poziomu `try` / `catch` bloku.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)