---
title: 'Projektant przepływu pracy — jak: Używanie projektanta argumentów'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebaa9211df2f4b7f734634d5d13b6344c32ba6ef
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976995"
---
# <a name="how-to-use-the-argument-designer"></a>Instrukcje: Używanie projektanta argumentów

W porównaniu do poprzednich wersji programu .NET Framework, projektanta argumentów ułatwia Zezwalaj na dane przesyłane do i z działania. Projektant jest dostępne po kliknięciu **argumenty** przycisku w lewym dolnym rogu obszaru roboczego projektowania. Projektant zawiera listę argumentów, które są wyświetlane w formie tabelarycznej można sortować według wszystkich nagłówków kolumn, z wyjątkiem **wartość domyślna** kolumny. Każdy argument zawiera nazwę, kierunku w/out/w out/właściwości, typ i domyślne wyrażenie wartości (jeśli istnieje). Nazwa i wartość domyślną wyrażenia są polami tekst do edycji, a typ i kierunek są list rozwijanych. Aby uzyskać więcej informacji, zobacz [zmienne i argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Aby utworzyć nowy argument

1.  Otwórz rozwiązanie, przepływ pracy lub działania w programie Visual Studio.

2.  Otwórz projektanta argumentów, klikając pozycję **argumenty** przycisku w lewym dolnym rogu obszaru roboczego projektowania. Pojawi się Projektant argumentów.

3.  Kliknij pusty wiersz etykietą **Utwórz Argument**. Spowoduje to dodanie nowego wiersza z argumentem nowe, używając następujących wartości domyślne: argumentx dla **nazwa** gdzie x jest liczbą całkowitą o początkowej wartości 1, który jest automatycznie zwiększany do tworzenia nazw unikatowych argument **w**  dla **kierunek**, i **ciąg** dla **typ argumentu**. Wartość nie jest dodawany do **wartość domyślna**. Wartości te można zmienić w dowolnym momencie podczas procesu projektowania przepływu pracy.

    > [!NOTE]
    > Aby usunąć argumentu, wybierz argument, klikając go, a następnie naciśnij klawisz **Usuń** klucza.

## <a name="see-also"></a>Zobacz także

- [Używanie projektanta przepływu pracy](developing-applications-with-the-workflow-designer.md)
- [Zmienne i argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)