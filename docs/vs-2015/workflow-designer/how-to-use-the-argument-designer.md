---
title: 'Instrukcje: korzystanie z projektanta argumentów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659112"
---
# <a name="how-to-use-the-argument-designer"></a>Instrukcje: Używanie projektanta argumentów
W porównaniu do poprzednich wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , Projektant argumentów ułatwia, aby dane były przesyłane do i z działania. Dostęp do projektanta można uzyskać, klikając przycisk **argumenty** w lewym dolnym rogu kanwy projektowania. Projektant zawiera listę argumentów, które pojawiają się w formie tabelarycznej i mogą być sortowane według poszczególnych nagłówków kolumn, z wyjątkiem kolumny **wartości domyślnej** . Każdy argument zawiera nazwę, wartość we/wychodzącą/out/lub właściwość, typ i wyrażenie domyślne (jeśli istnieje). Nazwa i domyślne wartości wyrażenia są edytowalnymi polami tekstowymi, a typ i kierunek są rozwijane. [!INCLUDE[crabout](../includes/crabout-md.md)] argumenty, zobacz [zmienne i argumenty](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>Aby utworzyć nowy argument

1. Otwórz rozwiązanie przepływu pracy lub działania w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

2. Otwórz projektanta argumentów, klikając przycisk **argumenty** w lewym dolnym rogu kanwy projektowania. Zostanie wyświetlony Projektant argumentów.

3. Kliknij pusty wiersz z etykietą **Utwórz**. Spowoduje to dodanie nowego wiersza z nowym argumentem przy użyciu następujących wartości domyślnych: argumentx dla **nazwy** , gdzie x jest liczbą całkowitą z wartością początkową 1, która jest automatycznie zwiększana w celu utworzenia unikatowych nazw argumentów, **w** odniesieniu do **kierunku**i **ciągu** dla **typu argumentu**. Żadna wartość nie jest dodawana do **wartości domyślnej**. Te wartości można zmienić w dowolnym momencie podczas procesu projektowania przepływu pracy.

    > [!NOTE]
    > Aby usunąć argument, zaznacz go, klikając go, a następnie naciśnij klawisz **delete** .

## <a name="see-also"></a>Zobacz też
 [Używanie Projektant przepływu pracy](../workflow-designer/using-the-workflow-designer.md) [zmiennych i argumentów](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)