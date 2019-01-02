---
title: Zmiany zwracanego typu metody DataContext nie można cofnąć
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: e133a609b8e3a0b8b47d0c2ea7408d7c3e9bd9c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947780"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Zmiany zwracanego typu metody DataContext nie można cofnąć

Zmiany zwracanego typu metody DataContext nie można cofnąć. Aby przywrócić automatycznie wygenerowany typ, należy przeciągnąć element z **Eksploratora serwera** lub **Eksplorator bazy danych** do ponownie za pomocą Projektanta obiektów relacyjnych. Czy na pewno chcesz zmienić zwracany typ?

Zwracany typ <xref:System.Data.Linq.DataContext> metoda zależy od tego, gdzie można upuścić elementu w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Jeśli usuniesz element bezpośrednio na istniejącej klasy jednostki, <xref:System.Data.Linq.DataContext> metodę, która ma typ zwracany klasy jednostki zostanie utworzony. Jeśli usuniesz element na pustym obszarem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], <xref:System.Data.Linq.DataContext> metodę, która zwraca automatycznie wygenerowany typ zostanie utworzony. Możesz zmienić typ zwracany <xref:System.Data.Linq.DataContext> metoda po dodaniu do okienka metod. Aby sprawdzić lub zmienić typ zwracany <xref:System.Data.Linq.DataContext> metody, zaznacz go i kliknij **typie zwracanym** właściwość **właściwości** okna.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Aby zmienić zwracany typ DataContext

- Kliknij przycisk **Tak**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Aby zamknąć okno komunikatu i pozostaw bez zmian typu zwracanego

- Kliknij przycisk **nie**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Aby powrócić do oryginalnego typu zwracanego po zmianie typu zwracanego

1. Wybierz <xref:System.Data.Linq.DataContext> metody [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] i usuń go.

2. Znajdź element w **Server Explorer/Eksploratorze bazy danych** i przeciągnij go na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    A <xref:System.Data.Linq.DataContext> metody jest tworzony przy użyciu oryginalnego domyślny typ zwracany.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)