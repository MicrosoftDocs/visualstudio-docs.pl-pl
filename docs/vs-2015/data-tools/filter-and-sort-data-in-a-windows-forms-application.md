---
title: Filtrowanie i sortowanie danych w aplikacji Windows Forms | Microsoft Docs
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
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24c623efc141ff84c2585f967596271d1efbc502
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671649"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrowanie i sortowanie danych w aplikacji Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Filtrowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości na wyrażenie ciągu zwracające żądane rekordy.

 Dane są sortowane przez ustawienie <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwości na nazwę kolumny, według której ma zostać wykonane sortowanie; Dołącz `DESC` do sortowania w kolejności malejącej lub Dołącz `ASC` do sortowania w porządku rosnącym.

> [!NOTE]
> Jeśli aplikacja nie korzysta ze <xref:System.Windows.Forms.BindingSource> składników, można filtrować i sortować dane za pomocą <xref:System.Data.DataView> obiektów. Aby uzyskać więcej informacji, zobacz temat [DataViews](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Aby odfiltrować dane za pomocą składnika BindingSource

- Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość na wyrażenie, które ma zostać zwrócone. Na przykład poniższy kod zwraca klientów z systemem `CompanyName` , który zaczyna się od "B":

     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Aby posortować dane za pomocą składnika BindingSource

- Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość na kolumnę, według której ma zostać wykonane sortowanie. Na przykład poniższy kod sortuje klientów w `CompanyName` kolumnie w kolejności malejącej:

     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
