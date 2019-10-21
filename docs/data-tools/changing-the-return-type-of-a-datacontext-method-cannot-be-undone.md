---
title: Zmiany zwracanego typu metody DataContext nie można cofnąć
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 95d75e084b4824cf7cc8e717b1ce9174e76aa2e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648689"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Zmiany zwracanego typu metody DataContext nie można cofnąć

Nie można cofnąć zwracanego typu metody DataContext. Aby powrócić do automatycznie generowanego typu, należy ponownie przeciągnąć element z **Eksplorator serwera** lub **Eksplorator bazy danych** do projektanta O/R. Czy na pewno chcesz zmienić zwracany typ?

Zwracany typ metody <xref:System.Data.Linq.DataContext> różni się w zależności od tego, gdzie porzucasz element w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. W przypadku porzucenia elementu bezpośrednio do istniejącej klasy jednostki zostanie utworzona Metoda <xref:System.Data.Linq.DataContext>, która ma zwracany typ klasy jednostki. W przypadku usunięcia elementu do pustego obszaru [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] zostanie utworzony <xref:System.Data.Linq.DataContext> Metoda zwracająca automatycznie wygenerowany typ. Zwracany typ metody <xref:System.Data.Linq.DataContext> można zmienić po dodaniu jej do okienka metody. Aby sprawdzić lub zmienić zwracany typ metody <xref:System.Data.Linq.DataContext>, zaznacz ją, a następnie kliknij właściwość **Typ zwracany** w oknie **Właściwości** .

## <a name="to-change-the-return-type-of-a-datacontext"></a>Aby zmienić zwracany typ elementu DataContext

- Kliknij przycisk **Tak**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Aby wyjść z okna komunikatu i pozostawić niezmieniony typ zwracany

- Kliknij przycisk **nie**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Aby powrócić do oryginalnego typu zwracanego po zmianie zwracanego typu

1. Wybierz metodę <xref:System.Data.Linq.DataContext> na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] i usuń ją.

2. Znajdź element w **Eksplorator serwera/Eksplorator bazy danych** i przeciągnij go na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    Metoda <xref:System.Data.Linq.DataContext> jest tworzona przy użyciu oryginalnego domyślnego typu zwracanego.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)