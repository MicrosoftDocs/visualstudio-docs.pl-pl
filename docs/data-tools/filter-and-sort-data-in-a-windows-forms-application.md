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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 596397cc22cf0f0134463256c0861127dcfb81e1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586617"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrowanie i sortowanie danych w aplikacji Windows Forms

Filtrowanie danych przez ustawienie właściwości <xref:System.Windows.Forms.BindingSource.Filter%2A> na wyrażenie ciągu zwracające odpowiednie rekordy.

Dane są sortowane przez ustawienie właściwości <xref:System.Windows.Forms.BindingSource.Sort%2A> na nazwę kolumny, w której ma zostać wykonane sortowanie. Dołącz `DESC`, aby posortować w kolejności malejącej, lub Dołącz `ASC`, aby posortować w kolejności rosnącej.

> [!NOTE]
> Jeśli aplikacja nie używa składników <xref:System.Windows.Forms.BindingSource>, można filtrować i sortować dane przy użyciu obiektów <xref:System.Data.DataView>. Aby uzyskać więcej informacji, zobacz temat [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Aby odfiltrować dane za pomocą składnika BindingSource

- Ustaw właściwość <xref:System.Windows.Forms.BindingSource.Filter%2A> na wyrażenie, które ma zostać zwrócone. Na przykład poniższy kod zwraca klientów z `CompanyName`, który rozpoczyna się od "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Aby posortować dane za pomocą składnika BindingSource

- Ustaw właściwość <xref:System.Windows.Forms.BindingSource.Sort%2A> na kolumnę, według której ma zostać wykonane sortowanie. Na przykład poniższy kod sortuje klientów w kolumnie `CompanyName` w kolejności malejącej:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
