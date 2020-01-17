---
title: Nie można usunąć wybranej klasy, ponieważ jest ona używana jako zwracany typ przez co najmniej jedną metodę DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 249a5338985983509f04e0ff268b2f30e2773f71
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113563"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Nie można usunąć wybranej klasy, ponieważ jest ona używana jako zwracany typ przez co najmniej jedną metodę DataContext

Typ zwracany jednej lub więcej metod <xref:System.Data.Linq.DataContext> jest wybraną klasą jednostki. Usunięcie klasy jednostki, która jest używana jako zwracany typ metody <xref:System.Data.Linq.DataContext> powoduje niepowodzenie kompilacji projektu. Aby usunąć wybraną klasę jednostki, zidentyfikuj metody <xref:System.Data.Linq.DataContext>, które go używają, i ustaw ich typy zwracane na inną klasę jednostki.

Aby przywrócić typy zwracane <xref:System.Data.Linq.DataContext> metod do ich oryginalnych typów generowanych automatycznie, najpierw Usuń metodę <xref:System.Data.Linq.DataContext> z okienka **metody** , a następnie przeciągnij obiekt z **Eksplorator serwera**/**Eksplorator bazy danych** ponownie do **projektanta o/R** .

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Zidentyfikuj metody <xref:System.Data.Linq.DataContext>, które używają klasy Entity jako typu zwracanego przez wybranie metody <xref:System.Data.Linq.DataContext> w okienku **metody** i sprawdzanie właściwości **typu zwracanego** w oknie **Właściwości** .

2. Ustaw **zwracany typ** na inną klasę jednostki lub usuń metodę <xref:System.Data.Linq.DataContext> z okienka metody.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
