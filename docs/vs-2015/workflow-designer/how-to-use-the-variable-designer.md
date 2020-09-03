---
title: 'Instrukcje: korzystanie z projektanta zmiennych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4744864824da5efb238e9af1a5a12fcef79ea4ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659073"
---
# <a name="how-to-use-the-variable-designer"></a>Instrukcje: Używanie projektanta zmiennych
Projektant zmiennych służy do tworzenia zmiennych do użycia w scenariuszach powiązań danych i instrukcjach warunkowych. Dostęp do projektanta można uzyskać, klikając przycisk **zmienne** w lewym dolnym rogu kanwy projektowania. Projektant zawiera listę zmiennych, które są wyświetlane w formie tabelarycznej i mogą być posortowane według poszczególnych nagłówków kolumn, z wyjątkiem kolumny **domyślnej** . Każda zmienna zawiera nazwę, typ zmiennej, zakres i wartość domyślną (jeśli istnieje). Nazwa i wartość domyślna są edytowalnymi polami tekstowymi, a typ i zakres są rozwijane. Zakres to działanie, które zostało wybrane podczas wywoływania projektanta zmiennych. Jeśli zmienna nie może zostać utworzona w ramach zakresu zaznaczenia, zakres domyślnie będzie najbliższym działaniem nadrzędnym zaznaczenia, które pozwala na tworzenie zmiennych w swoim zakresie. [!INCLUDE[crabout](../includes/crabout-md.md)] zmienne, zobacz [zmienne i argumenty](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

 Kolejność sortowania nie zostanie zastosowana, dopóki użytkownik jawnie nie użyje kontrolki sortowania, zamknie i ponownie otworzy projektanta zmiennych lub utworzy kolejną zmienną.

### <a name="to-create-a-new-variable"></a>Aby utworzyć nową zmienną

1. Otwórz rozwiązanie przepływu pracy lub działania w programie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

2. Na kanwie projektowania wybierz działanie w przepływie pracy.

3. Otwórz projektanta zmiennych, klikając przycisk **zmienne** w lewym dolnym rogu kanwy projektowania. Zostanie wyświetlony Projektant zmiennych.

4. Kliknij pusty wiersz z etykietą **Utwórz zmienną**. Spowoduje to dodanie nowego wiersza z nową zmienną przy użyciu następujących wartości domyślnych: variablex dla **nazwy** , gdzie x jest liczbą całkowitą z wartością początkową 1, która jest automatycznie zwiększana w celu utworzenia unikatowych nazw zmiennych, **ciągu** dla **typu zmiennej**i **sekwencji** dla **zakresu**. Żadna wartość nie jest dodawana **Domyślnie**. Te wartości można zmienić w dowolnym momencie podczas procesu projektowania przepływu pracy.

    > [!NOTE]
    > Aby usunąć zmienną, wybierz ją, klikając ją, a następnie naciśnij klawisz **delete** .

## <a name="see-also"></a>Zobacz też
 [Używanie](../workflow-designer/using-the-workflow-designer.md) [zmiennych Projektant przepływu pracy i argumentów](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) [jak: korzystanie z projektanta argumentów](../workflow-designer/how-to-use-the-argument-designer.md)