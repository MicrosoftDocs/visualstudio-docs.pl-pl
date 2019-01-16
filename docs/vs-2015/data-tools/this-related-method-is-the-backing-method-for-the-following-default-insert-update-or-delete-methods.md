---
title: Ta powiązana metoda to metoda zapasowa następujących domyślne metod wstawiania, aktualizacji lub usuń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 34c44a8d47ab1694b2af7accd76ef5432668a212
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "49259145"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Ta powiązana metoda to metoda zapasowa następujących domyślne metod wstawiania, aktualizacji lub Usuń. Jeśli zostanie usunięta, te metody także zostaną usunięte. Czy chcesz kontynuować?  
  
 Wybrane `DataContext` metoda jest obecnie używany jako jedną z metod Insert, Update lub Delete dla jednej z klas obiektów w Projektancie obiektów relacyjnych. Trwa usuwanie wybranej metody spowodować, że klasa jednostki, która została przy użyciu tej metody, aby powrócić do domyślnego zachowania czasu wykonywania do operacji Insert, Update, lub usunąć w trakcie aktualizacji.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Można usunąć wybranej metody, powodując Klasa jednostki użyć aktualizacje środowiska uruchomieniowego  
  
-   Kliknij przycisk **Tak**.  
  
     Wybranej metody zostanie usunięty, a wszystkie klasy, które umożliwiający zastępowanie zachowania aktualizacji tej metody są przywracane przy użyciu domyślnego LINQ do zachowania w czasie wykonywania SQL.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Aby zamknąć okno komunikatu, pozostawiając wybranej metody bez zmian  
  
-   Kliknij przycisk **nie**.  
  
     Zamyka okno komunikatu, i są wprowadzane żadne zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

