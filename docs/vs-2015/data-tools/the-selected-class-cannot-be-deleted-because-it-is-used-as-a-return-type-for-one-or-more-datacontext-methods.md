---
title: Nie można usunąć wybranej klasy, ponieważ jest używany jako typ zwracany dla co najmniej jedną metodę DataContext | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03e1df5398b4a23a1633d4a0fa92fe0bedb830f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686627"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Nie można usunąć wybranej klasy, ponieważ jest ona używana jako zwracany typ przez co najmniej jedną metodę DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typ zwracany co najmniej jeden <xref:System.Data.Linq.DataContext> metody jest klasą wybranej jednostki. Usuwanie klasę jednostki, która jest używana jako typ zwracany dla <xref:System.Data.Linq.DataContext> metoda spowoduje, że kompilacja projektu nie powiedzie się. Aby usunąć klasy wybranej jednostki, określ <xref:System.Data.Linq.DataContext> metody, które go używać i ustawiać zwracanym typem klasy innej jednostki.  
  
 Aby przywrócić typów zwracanych <xref:System.Data.Linq.DataContext> metody służące do ich oryginalnej typów generowanych automatycznie, należy najpierw usunąć <xref:System.Data.Linq.DataContext> metody z okienko metod, a następnie przeciągnij obiekt z **Eksploratora serwera** / **Eksplorator bazy danych** do ponownie za pomocą Projektanta obiektów relacyjnych.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Identyfikowanie <xref:System.Data.Linq.DataContext> metody, które używają klas jednostek jako zwracany typ, wybierając <xref:System.Data.Linq.DataContext> metody w metodach okienka i zapoznanie się **typie zwracanym** właściwości w **właściwości** okna .  
  
2. Ustaw **typie zwracanym** do klasy innej jednostki lub usuń <xref:System.Data.Linq.DataContext> metody z okienko metod.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Przewodnik: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Instrukcje: Zmienianie zwracanego typu metody DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
