---
title: Nie można cofnąć typu zwracanego metody DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f020aed4c1213d3db008862386704c0f63b86bde
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662468"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Zmiany zwracanego typu metody DataContext nie można cofnąć
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nie można cofnąć zwracanego typu metody DataContext. Aby powrócić do automatycznie generowanego typu, należy ponownie przeciągnąć element z Eksplorator serwera/Eksplorator bazy danych do projektanta O/R. Czy na pewno chcesz zmienić zwracany typ?

 Zwracany typ <xref:System.Data.Linq.DataContext> metody różni się w zależności od tego, gdzie porzucasz element w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . W przypadku porzucenia elementu bezpośrednio do istniejącej klasy jednostki <xref:System.Data.Linq.DataContext> tworzona jest metoda, która ma zwracany typ klasy jednostki. Jeśli upuszczasz element na pusty obszar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , <xref:System.Data.Linq.DataContext> zostanie utworzona Metoda zwracająca automatycznie wygenerowany typ. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu jej do okienka metod. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz ją i kliknij właściwość **Typ zwracany** w oknie **Właściwości** .

### <a name="to-change-the-return-type-of-a-datacontext"></a>Aby zmienić zwracany typ elementu DataContext

- Kliknij przycisk **Yes** (Tak).

### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Aby wyjść z okna komunikatu i pozostawić niezmieniony typ zwracany

- Kliknij przycisk **nie**.

### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Aby powrócić do oryginalnego typu zwracanego po zmianie zwracanego typu

1. Wybierz <xref:System.Data.Linq.DataContext> metodę z [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] i usuń ją.

2. Znajdź element w **Eksplorator serwera/Eksplorator bazy danych** i przeciągnij go na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

     <xref:System.Data.Linq.DataContext>Metoda jest tworzona przy użyciu oryginalnego domyślnego typu zwracanego.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [metodach DataContext programu Visual Studio (Projektant o/r)](../data-tools/datacontext-methods-o-r-designer.md) [instrukcje: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (projektant o/r)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
