---
title: Wyłącz ograniczenia podczas wypełniania zestawu danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667170"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Wyłączanie ograniczeń podczas zapełniania zestawu danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli zestaw danych zawiera ograniczenia (takie jak ograniczenia FOREIGN KEY), theycan zgłasza błędy związane z kolejnością operacji wykonywanych względem zestawu danych. Na przykład ładowanie rekordów podrzędnych przed loadingrelated rekordy nadrzędne może naruszać ograniczenie i spowodować błąd. Gdy tylko załadujesz rekord podrzędny, ograniczenie sprawdza pokrewny rekord nadrzędny i zgłasza błąd.

 Jeśli nie było żadnego mechanizmu zezwalania na tymczasowe ograniczenie ograniczeń, wystąpi błąd przy każdej próbie załadowania rekordu do tabeli podrzędnej. Innym sposobem zawieszenia wszystkich ograniczeń w zestawie danych jest z <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> właściwościami i.

> [!NOTE]
> Zdarzenia walidacji (na przykład <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> ) nie będą zgłaszane, gdy ograniczenia są wyłączone.

### <a name="to-suspend-update-constraints-programmatically"></a>Aby programowo wstrzymać ograniczenia dotyczące aktualizacji

- Poniższy przykład pokazuje, jak tymczasowo wyłączyć sprawdzanie ograniczeń w zestawie danych:

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Aby zawiesić ograniczenia aktualizacji przy użyciu Projektant obiektów Dataset

1. Otwórz zestaw danych w Projektant obiektów Dataset. Aby uzyskać więcej informacji, zobacz [jak: otwieranie zestawu danych w Projektant obiektów DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. W oknie **Właściwości** Ustaw <xref:System.Data.DataSet.EnforceConstraints%2A> Właściwość na `false` .

## <a name="see-also"></a>Zobacz też
 [Wypełnianie zestawów danych przy użyciu relacji TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) [w zestawach danych](../data-tools/relationships-in-datasets.md)
