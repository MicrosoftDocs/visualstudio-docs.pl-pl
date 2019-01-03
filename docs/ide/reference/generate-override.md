---
title: Generowanie zastąpienia — metoda
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f4c78edaecb9cedf3bcff4acf7b39b3e54701f24
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906868"
---
# <a name="generate-an-override-in-visual-studio"></a>Generowanie zastąpienia w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe generowania kodu dla dowolnej metody, która może być zastąpiona z klasy bazowej.

**Kiedy:** Chcesz przesłonić metody klasy bazowej i generowania podpisu automatycznie.

**Dlaczego:** Można napisać podpis metody samodzielnie, ale tej funkcji będzie generowana automatycznie podpis.

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