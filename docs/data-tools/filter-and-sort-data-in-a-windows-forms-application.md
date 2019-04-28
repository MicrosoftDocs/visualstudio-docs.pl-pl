---
title: Filtrowanie i sortowanie danych w aplikacji Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 17416a3b64d6cbb5f01192440a9df735f0b9fb94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566732"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrowanie i sortowanie danych w aplikacji Windows Forms

Filtrowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwość wyrażeniem, które zwraca żądane rekordy.

Sortowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwość na nazwę kolumny, na którym mają być sortowane; Dołącz `DESC` można sortować w kolejności malejącej lub dołączyć `ASC` sortowanie w kolejności rosnącej.

> [!NOTE]
> Jeśli aplikacja nie korzysta z <xref:System.Windows.Forms.BindingSource> składników, można filtrować i sortować dane przy użyciu <xref:System.Data.DataView> obiektów. Aby uzyskać więcej informacji, zobacz [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Aby filtrować dane za pomocą składnika BindingSource

- Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwość na wyrażenie, które mają być zwracane. Na przykład, poniższy kod zwraca klientom `CompanyName` który zaczyna się od "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Aby posortować dane za pomocą składnika BindingSource

- Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwość kolumnę, która ma zostać wykonane sortowanie. Na przykład, poniższy kod sortuje klientom na `CompanyName` kolumny w kolejności malejącej:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)