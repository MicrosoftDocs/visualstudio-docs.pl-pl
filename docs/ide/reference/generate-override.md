---
title: Generuj przesłonięcie metody
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569247"
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

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
