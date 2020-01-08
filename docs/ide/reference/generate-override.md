---
title: Generowanie zastąpienia — metoda
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569247"
---
# <a name="generate-an-override-in-visual-studio"></a>Generowanie zastąpienia w programie Visual Studio

Dotyczy to generowanie kodu:

- Język C#

- Język Visual Basic

**Co:** pozwala natychmiast generowania kodu dla dowolnej metody, która może być zastąpiona z klasy bazowej.

**Kiedy:** chcesz przesłonić metody klasy bazowej i generowania podpisu automatycznie.

**Dlaczego:** można napisać podpis metody samodzielnie, ale tej funkcji będzie generowana automatycznie podpis.

## <a name="how-to"></a>Instrukcje

1. Typ `override` w C# lub `Overrides` w języku Visual Basic, spację, gdzie chcesz wstawić to metoda przesłonięcia.

   - C#:

      ![Zastąp IntelliSenseC#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Zastąp funkcję IntelliSense w języku VB](media/override-intellisense-vb.png)

2. Wybierz metodę, którą chcesz zastąpić z klasy bazowej.

   > [!TIP]
   > - Użyj ikony właściwości ![Ikona Właściwość](media/override-property-cs.png) Aby pokazać lub ukryć właściwości na liście.
   > - Użyj ikony — metoda ![Ikona metody](media/override-method-cs.png) Aby pokazać lub ukryć metody na liście.

   Wybrane metody lub właściwości jest dodawana do klasy jako przesłonięcie, gotowy do zaimplementowania.

   - C#:

       ![Zastąp wynikC#](media/override-result-cs.png)

   - Visual Basic:

       ![Zastąp wynik VB](media/override-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
