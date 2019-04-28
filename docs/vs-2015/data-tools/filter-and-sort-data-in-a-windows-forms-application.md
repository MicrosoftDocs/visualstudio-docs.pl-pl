---
title: Filtrowanie i sortowanie danych w aplikacji Windows Forms | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e0d0ca917839ea71d6062dc8d9a5a689bbc3d241
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431912"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrowanie i sortowanie danych w aplikacji Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Filtrowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwość wyrażeniem, które zwraca żądane rekordy.  
  
 Sortowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwość na nazwę kolumny należy do sortowania; Dołącz `DESC` można sortować w kolejności malejącej lub dołączyć `ASC` sortowanie w kolejności rosnącej.  
  
> [!NOTE]
> Jeśli aplikacja nie korzysta z <xref:System.Windows.Forms.BindingSource> składników, można filtrować i sortować dane przy użyciu <xref:System.Data.DataView> obiektów. Aby uzyskać więcej informacji, zobacz [DataView](http://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Aby filtrować dane za pomocą składnika BindingSource  
  
- Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwość na wyrażenie, które mają być zwracane. Na przykład, poniższy kod zwraca klientom `CompanyName` który zaczyna się od "B":  
  
     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Aby posortować dane za pomocą składnika BindingSource  
  
- Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwość kolumnę, która ma zostać wykonane sortowanie. Na przykład, poniższy kod sortuje klientom na `CompanyName` kolumny w kolejności malejącej:  
  
     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
