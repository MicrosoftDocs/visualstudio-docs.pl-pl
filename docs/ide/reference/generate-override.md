---
title: Generowanie zastępowania metody
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569247"
---
# <a name="generate-an-override-in-visual-studio"></a>Generowanie zastąpienia w programie Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla dowolnej metody, która może zostać zastąpiona z klasy podstawowej.

**Kiedy:** Chcesz zastąpić metodę klasy podstawowej i automatycznie wygenerować podpis.

**Dlaczego?** Podpis metody można napisać samodzielnie, jednak ta funkcja wygeneruje podpis automatycznie.

## <a name="how-to"></a>Porady

1. Wpisz `override` w języku `Overrides` C# lub visual basic, a następnie spacja, gdzie chcesz wstawić metodę zastępowania.

   - C#:

      ![Zastępowanie intellisense C #](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Zastępowanie intellisense VB](media/override-intellisense-vb.png)

2. Wybierz metodę, którą chcesz zastąpić z klasy podstawowej.

   > [!TIP]
   > - Użyj ikony właściwości ![Ikona właściwości](media/override-property-cs.png) , aby wyświetlić lub ukryć właściwości na liście.
   > - Użyj ikony metody ![Ikona Metody](media/override-method-cs.png) , aby wyświetlić lub ukryć metody na liście.

   Wybrana metoda lub właściwość jest dodawany do klasy jako zastąpienie, gotowe do zaimplementowania.

   - C#:

       ![Zastądnie wyniku C #](media/override-result-cs.png)

   - Visual Basic:

       ![Zastępowanie wyniku VB](media/override-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
