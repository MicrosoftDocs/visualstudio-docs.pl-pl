---
title: 'Projektant przepływu pracy — jak: korzystanie z projektanta argumentów'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c3f8216bb0dfe3813e4852151c351b865128d0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650293"
---
# <a name="how-to-use-the-argument-designer"></a>Instrukcje: korzystanie z projektanta argumentów

Projektant argumentów ułatwia, aby dane były przesyłane do i z działania. Dostęp do projektanta, klikając przycisk **argumenty** w lewym dolnym rogu kanwy projektowania. Projektant zawiera listę argumentów, które pojawiają się w formie tabelarycznej i mogą być sortowane według poszczególnych nagłówków kolumn, z wyjątkiem kolumny **wartości domyślnej** . Każdy argument zawiera nazwę, wartość we/wychodzącą/out/lub właściwość, typ i wyrażenie domyślne (jeśli istnieje). Nazwa i domyślne wartości wyrażenia są edytowalnymi polami tekstowymi, a typ i kierunek są rozwijane. Aby uzyskać więcej informacji, zobacz [zmienne i argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Aby utworzyć nowy argument

1. Otwórz rozwiązanie przepływu pracy lub działania w programie Visual Studio.

2. Otwórz projektanta argumentów, klikając przycisk **argumenty** w lewym dolnym rogu kanwy projektowania. Zostanie wyświetlony Projektant argumentów.

3. Kliknij pusty wiersz z etykietą **Utwórz**. Spowoduje to dodanie nowego wiersza z nowym argumentem przy użyciu następujących wartości domyślnych: argumentx dla **nazwy** , gdzie x jest liczbą całkowitą z początkową wartością 1, która jest automatycznie zwiększana do tworzenia unikatowych nazw argumentów, **w** dla **kierunku** i **ciąg** dla **typu argumentu**. Żadna wartość nie jest dodawana do **wartości domyślnej**. Te wartości można zmienić w dowolnym momencie podczas procesu projektowania przepływu pracy.

    > [!NOTE]
    > Aby usunąć argument, zaznacz go, klikając go, a następnie naciśnij klawisz **delete** .

## <a name="see-also"></a>Zobacz także

- [Używanie projektanta przepływu pracy](developing-applications-with-the-workflow-designer.md)
- [Zmienne i argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)