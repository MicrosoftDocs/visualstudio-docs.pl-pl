---
title: Filtrowanie i sortowanie danych w aplikacji Windows Forms
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c420896a883146cf60de414100fc41080220e36
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282387"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrowanie i sortowanie danych w aplikacji Windows Forms

Filtrowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości na wyrażenie ciągu zwracające żądane rekordy.

Dane są sortowane przez ustawienie <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwości na nazwę kolumny, w której ma zostać wykonane sortowanie; Dołącz `DESC` do sortowania w kolejności malejącej lub Dołącz `ASC` do sortowania w porządku rosnącym.

> [!NOTE]
> Jeśli aplikacja nie korzysta ze <xref:System.Windows.Forms.BindingSource> składników, można filtrować i sortować dane za pomocą <xref:System.Data.DataView> obiektów. Aby uzyskać więcej informacji, zobacz temat [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Aby odfiltrować dane za pomocą składnika BindingSource

- Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość na wyrażenie, które ma zostać zwrócone. Na przykład poniższy kod zwraca klientów z systemem `CompanyName` , który zaczyna się od "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Aby posortować dane za pomocą składnika BindingSource

- Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość na kolumnę, według której ma zostać wykonane sortowanie. Na przykład poniższy kod sortuje klientów w `CompanyName` kolumnie w kolejności malejącej:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
