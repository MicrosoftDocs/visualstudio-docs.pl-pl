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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659112"
---
# <a name="how-to-use-the-argument-designer"></a>Instrukcje: korzystanie z projektanta argumentów
W porównaniu do poprzednich wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], Projektant argumentów ułatwia, aby dane były przesyłane do i z działania. Dostęp do projektanta można uzyskać, klikając przycisk **argumenty** w lewym dolnym rogu kanwy projektowania. Projektant zawiera listę argumentów, które pojawiają się w formie tabelarycznej i mogą być sortowane według poszczególnych nagłówków kolumn, z wyjątkiem kolumny **wartości domyślnej** . Każdy argument zawiera nazwę, wartość we/wychodzącą/out/lub właściwość, typ i wyrażenie domyślne (jeśli istnieje). Nazwa i domyślne wartości wyrażenia są edytowalnymi polami tekstowymi, a typ i kierunek są rozwijane. [!INCLUDE[crabout](../includes/crabout-md.md)] argumentów, zobacz [zmienne i argumenty](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>Aby utworzyć nowy argument

1. Otwórz rozwiązanie przepływu pracy lub działania w [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Otwórz projektanta argumentów, klikając przycisk **argumenty** w lewym dolnym rogu kanwy projektowania. Zostanie wyświetlony Projektant argumentów.

3. Kliknij pusty wiersz z etykietą **Utwórz**. Spowoduje to dodanie nowego wiersza z nowym argumentem przy użyciu następujących wartości domyślnych: argumentx dla **nazwy** , gdzie x jest liczbą całkowitą z początkową wartością 1, która jest automatycznie zwiększana do tworzenia unikatowych nazw argumentów, **w** dla **kierunku** i **ciąg** dla **typu argumentu**. Żadna wartość nie jest dodawana do **wartości domyślnej**. Te wartości można zmienić w dowolnym momencie podczas procesu projektowania przepływu pracy.

    > [!NOTE]
    > Aby usunąć argument, zaznacz go, klikając go, a następnie naciśnij klawisz **delete** .

## <a name="see-also"></a>Zobacz też
 [Używanie Projektant przepływu pracy](../workflow-designer/using-the-workflow-designer.md) [zmiennych i argumentów](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)