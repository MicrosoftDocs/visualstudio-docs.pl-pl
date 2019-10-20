---
title: Generuj przesłonięcie metody
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 075c7dc49ffba1d67bbb5b62d313f50b5d09e956
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668443"
---
# <a name="generate-an-override-in-visual-studio"></a>Generowanie przesłonięcia w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla dowolnej metody, która może zostać przesłonięta z klasy bazowej.

**Kiedy:** Chcesz przesłonić metodę klasy bazowej i wygenerować podpis automatycznie.

**Dlaczego:** Podpis metody można napisać samodzielnie, jednak ta funkcja będzie generować sygnaturę automatycznie.

## <a name="how-to"></a>Instrukcje

1. Wpisz `override` w C# lub `Overrides` w Visual Basic, po którym następuje spacja, gdzie chcesz wstawić metodę przesłonięcia.

   - C#:

      ![Zastąp funkcję IntelliSenseC#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Zastępowanie IntelliSense VB](media/override-intellisense-vb.png)

2. Wybierz metodę, która ma zostać przesłonięta z klasy bazowej.

   > [!TIP]
   > - Użyj ikony właściwości ![Ikona właściwości](media/override-property-cs.png) do wyświetlania lub ukrywania właściwości na liście.
   > - Użyj ikony metody ![Ikona metody](media/override-method-cs.png) , aby pokazać lub ukryć metody na liście.

   Wybrana metoda lub właściwość jest dodawana do klasy jako przesłonięcie, gotowy do zaimplementowania.

   - C#:

       ![Wynik przesłonięciaC#](media/override-result-cs.png)

   - Visual Basic:

       ![Przesłoń wynik VB](media/override-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)