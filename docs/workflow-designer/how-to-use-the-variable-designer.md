---
title: 'Projektant przepływu pracy — jak: Używanie projektanta zmiennych'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6d50fa27111cfb7f58c39cb29e7ff34038a1b6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959203"
---
# <a name="how-to-use-the-variable-designer"></a>Instrukcje: Używanie projektanta zmiennych

Projektanta zmiennych służy do tworzenia zmiennych do użytku w scenariuszach powiązanie danych i instrukcji warunkowych. Projektant jest dostępne po kliknięciu **zmienne** przycisku w lewym dolnym rogu obszaru roboczego projektowania. Projektant zawiera listę zmiennych, które są wyświetlane w formie tabelarycznej i mogą być sortowane przez każdy z nagłówków kolumn, z wyjątkiem **domyślne** kolumny. Każda zmienna zawiera nazwę, typ zmiennej, zakresu i wartość domyślną (jeśli istnieje). Nazwa i domyślne wartości są tekst do edycji i typie i zakresie są rozwijane. Zakres jest działania, który został wybrany, gdy wywołano projektanta zmiennych. Jeśli nie można utworzyć zmiennej w zakresie wyboru, zakres będzie domyślnie do najbliższej działania nadrzędnego zaznaczenia, umożliwiający zmiennych, które można utworzyć w swoim zakresie. Aby uzyskać więcej informacji, zobacz [zmienne i argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 Kolejność sortowania nie została zastosowana, dopóki użytkownik jawnie używa sortowania formantów, zostanie zamknięty i ponownie otwiera projektanta zmiennych lub tworzy innej zmiennej.

## <a name="to-create-a-new-variable"></a>Aby utworzyć nową zmienną

1.  Otwórz rozwiązanie, przepływ pracy lub działania w programie Visual Studio.

2.  W obszarze roboczym projektu wybierz działanie w przepływie pracy.

3.  Otwórz projektanta zmiennych, klikając pozycję **zmienne** przycisku w lewym dolnym rogu obszaru roboczego projektowania. Pojawi się projektanta zmiennych.

4.  Kliknij pusty wiersz etykietą **Tworzenie zmiennej**. Spowoduje to dodanie nowego wiersza przy użyciu nowej zmiennej, używając następujących wartości domyślne: variablex dla **nazwa** gdzie x jest liczbą całkowitą o początkowej wartości 1, który jest automatycznie zwiększany w celu tworzenia unikatowych nazw zmiennych,  **Ciąg** dla **typ zmiennej**, i **sekwencji** dla **zakres**. Wartość nie jest dodawany do **domyślne**. Wartości te można zmienić w dowolnym momencie podczas procesu projektowania przepływu pracy.

    > [!NOTE]
    > Aby usunąć zmienną, wybierz zmienną, klikając go, a następnie naciśnij klawisz **Usuń** klucza.

## <a name="see-also"></a>Zobacz także

- [Używanie projektanta przepływu pracy](developing-applications-with-the-workflow-designer.md)
- [Zmienne i argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Instrukcje: Używanie projektanta argumentów](../workflow-designer/how-to-use-the-argument-designer.md)