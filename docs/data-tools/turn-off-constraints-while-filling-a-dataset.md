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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9aca29de7e9c5a01e0c2caad2c42015cd31b3f75
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102864"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Wyłączanie ograniczeń podczas zapełniania zestawu danych

Jeśli zestaw danych zawiera ograniczenia (np. ograniczenia foreign key), mogą zgłaszać błędy związane z kolejnością operacje, które są wykonywane względem zestawu danych. Na przykład podczas ładowania rekordów podrzędnych przed załadowaniem związane z rekordów nadrzędnych można narusza ograniczenie i powodują wystąpienie błędu. Zaraz po załadowaniu podrzędnego rekordu ograniczenie sprawdza, czy rekord nadrzędny powiązane i zgłasza błąd.

Gdyby żaden mechanizm umożliwia zawieszenia tymczasowe ograniczenie błędu będzie uruchamiany za każdym razem, gdy próba załadowania rekordu do tabeli podrzędnej. Innym sposobem, aby wstrzymać wszystkie ograniczenia w zestawie danych jest <xref:System.Data.DataRow.BeginEdit%2A>, i <xref:System.Data.DataRow.EndEdit%2A> właściwości.

> [!NOTE]
> Zdarzenia walidacji (na przykład <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging>) nie zostaną wywołane, gdy ograniczenia są wyłączone.

## <a name="to-suspend-update-constraints-programmatically"></a>Aby programowo zawiesić Aktualizuj ograniczenia

- Poniższy przykład pokazuje, jak tymczasowo wyłączyć sprawdzanie w zestawie danych ograniczeń:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Zawieszenie ograniczenia aktualizacji za pomocą Projektanta obiektów Dataset

1. Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. W oknie **Właściwości** ustaw właściwość <xref:System.Data.DataSet.EnforceConstraints%2A> na `false`. 

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)