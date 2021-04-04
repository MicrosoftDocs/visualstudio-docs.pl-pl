---
title: Filtrowanie i sortowanie danych w aplikacji Windows Forms
description: Filtrowanie i sortowanie danych w aplikacji Windows Forms. Ustaw Właściwość Filter na wyrażenie ciągu zwracające żądane rekordy.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 045da0ade1ce60e2a8d21c24238c8e2b061e8612
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215828"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrowanie i sortowanie danych w aplikacji Windows Forms

Filtrowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości na wyrażenie ciągu zwracające żądane rekordy.

Dane są sortowane przez ustawienie <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwości na nazwę kolumny, w której ma zostać wykonane sortowanie; Dołącz `DESC` do sortowania w kolejności malejącej lub Dołącz `ASC` do sortowania w porządku rosnącym.

> [!NOTE]
> Jeśli aplikacja nie korzysta ze <xref:System.Windows.Forms.BindingSource> składników, można filtrować i sortować dane za pomocą <xref:System.Data.DataView> obiektów. Aby uzyskać więcej informacji, zobacz temat [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Aby odfiltrować dane za pomocą składnika BindingSource

- Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość na wyrażenie, które ma zostać zwrócone. Na przykład poniższy kod zwraca klientów z systemem `CompanyName` , który zaczyna się od "B":

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet6":::

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Aby posortować dane za pomocą składnika BindingSource

- Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość na kolumnę, według której ma zostać wykonane sortowanie. Na przykład poniższy kod sortuje klientów w `CompanyName` kolumnie w kolejności malejącej:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
