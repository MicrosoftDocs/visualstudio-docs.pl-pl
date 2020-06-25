---
title: Zmiany zwracanego typu metody DataContext nie można cofnąć
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d5b24337c9233aeeb060029cb54cd661b7591309
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282790"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Zmiany zwracanego typu metody DataContext nie można cofnąć

Nie można cofnąć zwracanego typu metody DataContext. Aby powrócić do automatycznie generowanego typu, należy ponownie przeciągnąć element z **Eksplorator serwera** lub **Eksplorator bazy danych** do projektanta O/R. Czy na pewno chcesz zmienić zwracany typ?

Zwracany typ <xref:System.Data.Linq.DataContext> metody różni się w zależności od tego, gdzie porzucasz element w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] . W przypadku porzucenia elementu bezpośrednio do istniejącej klasy jednostki <xref:System.Data.Linq.DataContext> tworzona jest metoda, która ma zwracany typ klasy jednostki. Jeśli upuszczasz element na pusty obszar [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , <xref:System.Data.Linq.DataContext> zostanie utworzona Metoda zwracająca automatycznie wygenerowany typ. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu jej do okienka metod. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz ją i kliknij właściwość **Typ zwracany** w oknie **Właściwości** .

## <a name="to-change-the-return-type-of-a-datacontext"></a>Aby zmienić zwracany typ elementu DataContext

- Kliknij przycisk **tak**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Aby wyjść z okna komunikatu i pozostawić niezmieniony typ zwracany

- Kliknij przycisk **nie**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Aby powrócić do oryginalnego typu zwracanego po zmianie zwracanego typu

1. Wybierz <xref:System.Data.Linq.DataContext> metodę z [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] i usuń ją.

2. Znajdź element w **Eksplorator serwera/Eksplorator bazy danych** i przeciągnij go na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] .

    <xref:System.Data.Linq.DataContext>Metoda jest tworzona przy użyciu oryginalnego domyślnego typu zwracanego.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)