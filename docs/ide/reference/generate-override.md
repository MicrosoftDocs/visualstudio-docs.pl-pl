---
title: Generuj przesłonięcie metody
description: Dowiedz się, jak natychmiast wygenerować kod dla każdej metody, która może zostać przesłonięta z klasy bazowej.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f27adacc39c53bf46b3a2ee09c71ae27b47f928
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617490"
---
# <a name="generate-an-override-in-visual-studio"></a>Generowanie przesłonięcia w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla dowolnej metody, która może zostać przesłonięta z klasy bazowej.

**Kiedy:** Chcesz przesłonić metodę klasy bazowej i wygenerować podpis automatycznie.

**Dlaczego:** Podpis metody można napisać samodzielnie, jednak ta funkcja będzie generować sygnaturę automatycznie.

## <a name="how-to"></a>Porady

1. Wpisz `override` w języku C# lub `Overrides` w Visual Basic, a po nim spację, gdzie chcesz wstawić metodę przesłaniania.

   - C#:

      ![Zastąp IntelliSense C #](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Zastępowanie IntelliSense VB](media/override-intellisense-vb.png)

2. Wybierz metodę, która ma zostać przesłonięta z klasy bazowej.

   > [!TIP]
   > - Użyj ikony właściwości ![Ikona właściwości](media/override-property-cs.png) do wyświetlania lub ukrywania właściwości na liście.
   > - Użyj ikony metody ![Ikona metody](media/override-method-cs.png) , aby pokazać lub ukryć metody na liście.

   Wybrana metoda lub właściwość jest dodawana do klasy jako przesłonięcie, gotowy do zaimplementowania.

   - C#:

       ![Przesłoń wynik C #](media/override-result-cs.png)

   - Visual Basic:

       ![Przesłoń wynik VB](media/override-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
