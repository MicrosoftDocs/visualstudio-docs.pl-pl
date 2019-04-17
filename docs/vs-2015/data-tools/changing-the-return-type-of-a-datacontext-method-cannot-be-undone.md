---
title: Zmiany zwracanego typu metody DataContext nie można cofnąć | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ba574854424eac14898c923701f7d8f4c1f81347
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648916"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Zmiany zwracanego typu metody DataContext nie można cofnąć
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zmiany zwracanego typu metody DataContext nie można cofnąć. Aby przywrócić automatycznie wygenerowany typ, można przeciągnąć element z Server Explorer/Eksploratorze bazy danych do Projektanta obiektów relacyjnych ponownie. Czy na pewno chcesz zmienić zwracany typ?  
  
 Zwracany typ <xref:System.Data.Linq.DataContext> metoda zależy od tego, gdzie można upuścić elementu w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Jeśli usuniesz element bezpośrednio na istniejącej klasy jednostki, <xref:System.Data.Linq.DataContext> metodę, która ma typ zwracany klasy jednostki zostanie utworzony. Jeśli usuniesz element na pustym obszarem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], <xref:System.Data.Linq.DataContext> metodę, która zwraca automatycznie wygenerowany typ zostanie utworzony. Możesz zmienić typ zwracany <xref:System.Data.Linq.DataContext> metoda po dodaniu do okienka metod. Aby sprawdzić lub zmienić typ zwracany <xref:System.Data.Linq.DataContext> metody, zaznacz go i kliknij **typie zwracanym** właściwość **właściwości** okna.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>Aby zmienić zwracany typ DataContext  
  
-   Kliknij przycisk **Tak**.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Aby zamknąć okno komunikatu i pozostaw bez zmian typu zwracanego  
  
-   Kliknij przycisk **nie**.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Aby powrócić do oryginalnego typu zwracanego po zmianie typu zwracanego  
  
1.  Wybierz <xref:System.Data.Linq.DataContext> metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] i usuń go.  
  
2.  Znajdź element w **Server Explorer/Eksploratorze bazy danych** i przeciągnij go na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     A <xref:System.Data.Linq.DataContext> metody jest tworzony przy użyciu oryginalnego domyślny typ zwracany.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Instrukcje: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
