---
title: Nie można usunąć wybranej klasy, ponieważ jest ona używana jako zwracany typ dla co najmniej jednej metody DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667256"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Nie można usunąć wybranej klasy, ponieważ jest ona używana jako zwracany typ przez co najmniej jedną metodę DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typ zwracany jednej lub więcej <xref:System.Data.Linq.DataContext> metod jest wybraną klasą jednostki. Usunięcie klasy jednostki, która jest używana jako zwracany typ dla metody, <xref:System.Data.Linq.DataContext> spowoduje niepowodzenie kompilacji projektu. Aby usunąć wybraną klasę jednostki, zidentyfikuj <xref:System.Data.Linq.DataContext> metody, które go używają, i ustaw ich typy zwracane na inną klasę jednostki.

 Aby przywrócić zwracane typy <xref:System.Data.Linq.DataContext> metod do ich oryginalnych typów generowanych automatycznie, należy najpierw usunąć <xref:System.Data.Linq.DataContext> metodę z okienka metody, a następnie ponownie przeciągnąć obiekt z **Eksplorator serwera** / **Eksplorator bazy danych** do projektanta O/R.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Zidentyfikuj <xref:System.Data.Linq.DataContext> metody, które używają klasy Entity jako typu zwracanego przez wybranie <xref:System.Data.Linq.DataContext> metody w okienku metody i sprawdzanie właściwości **typu zwracanego** w oknie **Właściwości** .

2. Ustaw **zwracany typ** na inną klasę jednostki lub Usuń <xref:System.Data.Linq.DataContext> metodę z okienka metody.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w](../data-tools/linq-to-sql-tools-in-visual-studio2.md) przewodniku po programie Visual Studio [: tworzenie klas LINQ to SQL (Projektant-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [metody DataContext (o/r](../data-tools/datacontext-methods-o-r-designer.md) Designer) [instrukcje: Zmienianie zwracanego typu metody DataContext (o/r Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
