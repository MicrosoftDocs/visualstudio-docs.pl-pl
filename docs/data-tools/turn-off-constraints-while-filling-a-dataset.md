---
title: Wyłączanie ograniczeń podczas zapełniania zestawu danych
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b8ab7bb827c478360a64d65f44af6770c77ebf77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648134"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Wyłączanie ograniczeń podczas zapełniania zestawu danych

Jeśli zestaw danych zawiera ograniczenia (takie jak ograniczenia FOREIGN KEY), mogą zgłaszać błędy związane z kolejnością operacji wykonywanych względem zestawu danych. Na przykład ładowanie rekordów podrzędnych przed załadowaniem powiązanych rekordów nadrzędnych może naruszać ograniczenie i spowodować błąd. Gdy tylko załadujesz rekord podrzędny, ograniczenie sprawdza pokrewny rekord nadrzędny i zgłasza błąd.

Jeśli nie było żadnego mechanizmu zezwalania na tymczasowe ograniczenie ograniczeń, wystąpi błąd przy każdej próbie załadowania rekordu do tabeli podrzędnej. Innym sposobem zawieszenia wszystkich ograniczeń w zestawie danych jest <xref:System.Data.DataRow.BeginEdit%2A>, a <xref:System.Data.DataRow.EndEdit%2A> właściwości.

> [!NOTE]
> Zdarzenia walidacji (na przykład <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging>) nie będą zgłaszane, gdy ograniczenia są wyłączone.

## <a name="to-suspend-update-constraints-programmatically"></a>Aby programowo wstrzymać ograniczenia dotyczące aktualizacji

- Poniższy przykład pokazuje, jak tymczasowo wyłączyć sprawdzanie ograniczeń w zestawie danych:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Aby zawiesić ograniczenia aktualizacji przy użyciu Projektant obiektów Dataset

1. Otwórz zestaw danych w **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. W oknie **Właściwości** ustaw właściwość <xref:System.Data.DataSet.EnforceConstraints%2A> na `false`.

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)