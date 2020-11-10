---
title: 'Projektant przepływu pracy — How to: Use the Variable Designer'
description: Dowiedz się, jak można użyć projektanta zmiennych do tworzenia zmiennych do użycia w scenariuszach powiązań danych i instrukcjach warunkowych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8dc5e402fcf3bedabe2b0f7fe606dfe807525ab
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437830"
---
# <a name="how-to-use-the-variable-designer"></a>Instrukcje: Używanie projektanta zmiennych

Projektant zmiennych służy do tworzenia zmiennych do użycia w scenariuszach powiązań danych i instrukcjach warunkowych. Dostęp do projektanta można uzyskać, klikając przycisk **zmienne** w lewym dolnym rogu kanwy projektowania. Projektant zawiera listę zmiennych, które są wyświetlane w formie tabelarycznej i mogą być posortowane według poszczególnych nagłówków kolumn, z wyjątkiem kolumny **domyślnej** . Każda zmienna zawiera nazwę, typ zmiennej, zakres i wartość domyślną (jeśli istnieje). Nazwa i wartość domyślna są edytowalnymi polami tekstowymi, a typ i zakres są rozwijane. Zakres to działanie, które zostało wybrane podczas wywoływania projektanta zmiennych. Jeśli zmienna nie może zostać utworzona w ramach zakresu zaznaczenia, zakres domyślnie będzie najbliższym działaniem nadrzędnym zaznaczenia, które pozwala na tworzenie zmiennych w swoim zakresie. Aby uzyskać więcej informacji, zobacz [zmienne i argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 Kolejność sortowania nie zostanie zastosowana, dopóki użytkownik jawnie nie użyje kontrolki sortowania, zamknie i ponownie otworzy projektanta zmiennych lub utworzy kolejną zmienną.

## <a name="to-create-a-new-variable"></a>Aby utworzyć nową zmienną

1. Otwórz rozwiązanie przepływu pracy lub działania w programie Visual Studio.

2. Na kanwie projektowania wybierz działanie w przepływie pracy.

3. Otwórz projektanta zmiennych, klikając przycisk **zmienne** w lewym dolnym rogu kanwy projektowania. Zostanie wyświetlony Projektant zmiennych.

4. Kliknij pusty wiersz z etykietą **Utwórz zmienną**. Spowoduje to dodanie nowego wiersza z nową zmienną przy użyciu następujących wartości domyślnych: variablex dla **nazwy** , gdzie x jest liczbą całkowitą z wartością początkową 1, która jest automatycznie zwiększana w celu utworzenia unikatowych nazw zmiennych, **ciągu** dla **typu zmiennej** i **sekwencji** dla **zakresu**. Żadna wartość nie jest dodawana **Domyślnie**. Te wartości można zmienić w dowolnym momencie podczas procesu projektowania przepływu pracy.

    > [!NOTE]
    > Aby usunąć zmienną, wybierz ją, klikając ją, a następnie naciśnij klawisz **delete** .

## <a name="see-also"></a>Zobacz też

- [Używanie projektanta przepływu pracy](developing-applications-with-the-workflow-designer.md)
- [Zmienne i argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Instrukcje: Używanie projektanta argumentów](../workflow-designer/how-to-use-the-argument-designer.md)
