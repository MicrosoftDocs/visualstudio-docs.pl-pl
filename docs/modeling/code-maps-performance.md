---
title: Mapy kodu są powolne
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12ba03ab97da3295a93b54dfc012d10fc012fd30
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57872391"
---
# <a name="improve-performance-for-code-maps"></a>Poprawianie wydajności dla map kodu

Podczas generowania mapy po raz pierwszy, program Visual Studio indeksuje wszystkie zależności, które znajdzie. Ten proces może zająć trochę czasu, szczególnie w przypadku dużych rozwiązań, ale zwiększa wydajność nowsze. Jeśli kod ulegnie zmianie, Visual Studio indeksuje ponownie tylko zaktualizowany kod. Aby zminimalizować czas potrzebny na mapie, aby zakończyć renderowania, należy wziąć pod uwagę poniższe sugestie:

- Mapowanie zależności, które Cię interesują.

- Przed wygenerowaniem mapy dla całego rozwiązania Zmniejsz zakres rozwiązania.

- Wyłącz automatyczne kompilacji dla rozwiązania, wybierając **pominięcia kompilacji** na pasku narzędzi mapy kodu.

- Wyłącz opcję automatycznego dodawania elementów nadrzędnych, wybierając **obejmują elementy nadrzędne** na pasku narzędzi mapy kodu.

   ![Przyciski pominięcia kompilacji i obejmują elementy nadrzędne](../modeling/media/codemapsfilterskipbuildicons.png)

- Edytuj plik mapy kodu bezpośrednio po to, aby usunąć węzły i łącza, które nie są potrzebne. Zmiana na mapie nie ma wpływu na odpowiedni kod. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Może upłynąć więcej czasu na tworzenie map lub dodanie elementów do mapy z **Eksploratora rozwiązań** gdy element projektu **Kopiuj do katalogu wyjściowego** właściwość jest ustawiona na **zawsze Kopiuj**. Aby zwiększyć wydajność, należy zmienić tę właściwość na **Kopiuj Jeśli nowszy** lub `PreserveNewest`. Zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md).

Mapa ukończone pokazuje zależności tylko w przypadku kodu pomyślnie utworzone. Jeśli wystąpią błędy kompilacji dla niektórych składników, te błędy są wyświetlane na mapie. Upewnij się, że składnik rzeczywiście kompiluje i ma zależności od tego, przed wprowadzeniem decyzji architektury oparte na mapie.