---
title: Mapy kodu są wolne
ms.date: 05/16/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8b3f889661cf0d1c775cd80dad61a92c3f5b60a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654177"
---
# <a name="improve-performance-for-code-maps"></a>Poprawianie wydajności map kodu

Po wygenerowaniu mapy po raz pierwszy, program Visual Studio indeksuje wszystkie zależności, które znajdzie. Ten proces może zająć trochę czasu, szczególnie w przypadku dużych rozwiązań, ale zwiększa wydajność. Jeśli kod ulegnie zmianie, program Visual Studio ponownie indeksuje tylko zaktualizowany kod. Aby zminimalizować czas potrzebny na zakończenie renderowania mapy, weź pod uwagę następujące sugestie:

- Mapuj tylko zależności, które Cię interesują.

- Przed wygenerowaniem mapy dla całego rozwiązania, Zmniejsz zakres rozwiązania.

- Wyłącz automatyczne Kompilowanie rozwiązania, wybierając pozycję **Pomiń kompilację** na pasku narzędzi mapy kodu.

- Wyłącz automatyczne dodawanie elementów nadrzędnych, wybierając pozycję **Dołącz** elementy nadrzędne na pasku narzędzi mapy kodu.

   ![Pomiń kompilację i Dołącz przyciski nadrzędne](../modeling/media/codemapsfilterskipbuildicons.png)

- Edytuj plik mapy kodu bezpośrednio, aby usunąć węzły i linki, które nie są potrzebne. Zmiana mapy nie ma wpływu na kod źródłowy. Aby dowiedzieć [się, jak dostosować mapy kodu, edytuj pliki DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Utworzenie map lub dodanie elementów do mapy z **Eksplorator rozwiązań** może zająć więcej czasu, gdy właściwość **Kopiuj do katalogu wyjściowego** elementu projektu jest ustawiona na wartość **Kopiuj zawsze**. Aby zwiększyć wydajność, należy zmienić tę właściwość na **Kopiuj, jeśli nowszy** lub `PreserveNewest`. Zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md).

Zakończona mapa pokazuje zależności tylko dla pomyślnie skompilowanego kodu. Jeśli wystąpią błędy kompilacji dla niektórych składników, te błędy są wyświetlane na mapie. Upewnij się, że składnik rzeczywiście kompiluje i ma zależności od tego przed podjęciem decyzji o architekturze na podstawie mapy.