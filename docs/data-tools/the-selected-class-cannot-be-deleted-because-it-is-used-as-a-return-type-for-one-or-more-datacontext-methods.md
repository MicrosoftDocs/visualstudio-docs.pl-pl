---
title: Nie można usunąć wybranej klasy
description: Nie można usunąć wybranej klasy, ponieważ jest ona używana jako zwracany typ przez co najmniej jedną metodę DataContext
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 84fabc7f0f1efdf06006597aec9bb813578589a8
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743251"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Nie można usunąć wybranej klasy, ponieważ jest ona używana jako zwracany typ przez co najmniej jedną metodę DataContext

Typ zwracany jednej lub więcej <xref:System.Data.Linq.DataContext> metod jest wybraną klasą jednostki. Usunięcie klasy jednostki, która jest używana jako zwracany typ dla metody, <xref:System.Data.Linq.DataContext> powoduje niepowodzenie kompilacji projektu. Aby usunąć wybraną klasę jednostki, zidentyfikuj <xref:System.Data.Linq.DataContext> metody, które go używają, i ustaw ich typy zwracane na inną klasę jednostki.

Aby przywrócić zwracane typy <xref:System.Data.Linq.DataContext> metod do ich oryginalnych typów generowanych automatycznie, należy najpierw usunąć <xref:System.Data.Linq.DataContext> metodę z okienka **metody** , a następnie ponownie przeciągnąć obiekt z **Eksplorator serwera** / **Eksplorator bazy danych** do **projektanta O/R** .

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Zidentyfikuj <xref:System.Data.Linq.DataContext> metody, które używają klasy Entity jako typu zwracanego przez wybranie <xref:System.Data.Linq.DataContext> metody w okienku **metody** i sprawdzanie właściwości **typu zwracanego** w oknie **Właściwości** .

2. Ustaw **zwracany typ** na inną klasę jednostki lub Usuń <xref:System.Data.Linq.DataContext> metodę z okienka metody.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
