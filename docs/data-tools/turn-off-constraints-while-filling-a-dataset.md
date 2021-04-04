---
title: Wyłączanie ograniczeń podczas zapełniania zestawu danych
description: Dowiedz się, jak wyłączyć ograniczenia podczas wypełniania zestawu danych. Wstrzymywanie ograniczeń aktualizacji programowo lub za pomocą Projektant obiektów Dataset.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 3280894ba1634f9775def74a88dcb413c94ba77a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215711"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Wyłączanie ograniczeń podczas zapełniania zestawu danych

Jeśli zestaw danych zawiera ograniczenia (takie jak ograniczenia FOREIGN KEY), mogą zgłaszać błędy związane z kolejnością operacji wykonywanych względem zestawu danych. Na przykład ładowanie rekordów podrzędnych przed załadowaniem powiązanych rekordów nadrzędnych może naruszać ograniczenie i spowodować błąd. Gdy tylko załadujesz rekord podrzędny, ograniczenie sprawdza pokrewny rekord nadrzędny i zgłasza błąd.

Jeśli nie było żadnego mechanizmu zezwalania na tymczasowe ograniczenie ograniczeń, wystąpi błąd przy każdej próbie załadowania rekordu do tabeli podrzędnej. Innym sposobem zawieszenia wszystkich ograniczeń w zestawie danych jest z <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> właściwościami i.

> [!NOTE]
> Zdarzenia walidacji (na przykład <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> ) nie będą zgłaszane, gdy ograniczenia są wyłączone.

## <a name="to-suspend-update-constraints-programmatically"></a>Aby programowo wstrzymać ograniczenia dotyczące aktualizacji

- Poniższy przykład pokazuje, jak tymczasowo wyłączyć sprawdzanie ograniczeń w zestawie danych:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet10":::

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Aby zawiesić ograniczenia aktualizacji przy użyciu Projektant obiektów Dataset

1. Otwórz zestaw danych w **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. W oknie **Właściwości** Ustaw <xref:System.Data.DataSet.EnforceConstraints%2A> Właściwość na `false` .

## <a name="see-also"></a>Zobacz też

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)
