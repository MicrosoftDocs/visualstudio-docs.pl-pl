---
title: Mapy kodu są powolne
description: Dowiedz się, jak poprawić wydajność mapy kodu i jak zminimalizować czas wymagany do zakończenia renderowania.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5a279a04b1bd76933df335bc0b2527ab4b2418f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389647"
---
# <a name="improve-performance-for-code-maps"></a>Poprawianie wydajności map kodu

Podczas generowania mapy po raz pierwszy Visual Studio indeksuje wszystkie znalezione zależności. Ten proces może zająć trochę czasu, szczególnie w przypadku dużych rozwiązań, ale zwiększa późniejszą wydajność. Jeśli kod się zmieni, Visual Studio ponownie indeksuje tylko zaktualizowany kod. Aby zminimalizować czas trwania renderowania mapy, rozważ następujące sugestie:

- Mapuj tylko zależności, które Cię interesują.

- Przed wygenerowaniem mapy dla całego rozwiązania zmniejsz zakres rozwiązania.

- Wyłącz automatyczną kompilację dla rozwiązania, wybierając pozycję **Pomiń kompilację** na pasku narzędzi mapy kodu.

- Wyłącz automatyczne dodawanie elementów nadrzędnych, wybierając pozycję **Uwzględnij elementy nadrzędne** na pasku narzędzi mapy kodu.

   ![Pomijanie przycisków kompilowania i dołączania rodziców](../modeling/media/codemapsfilterskipbuildicons.png)

- Edytuj plik mapy kodu bezpośrednio, aby usunąć węzły i linki, które nie są potrzebne. Zmiana mapy nie ma wpływu na kod źródłowy. Zobacz [Dostosowywanie map kodu przez edycję plików DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

Tworzenie map lub dodawanie elementów do mapy z usługi **Eksplorator rozwiązań** może zająć więcej  czasu, gdy właściwość Kopiuj do katalogu wyjściowego elementu projektu jest ustawiona na wartość Kopiuj **zawsze**. Aby zwiększyć wydajność, zmień tę właściwość na **Kopiuj, jeśli nowsze lub** `PreserveNewest` . Zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md).

Ukończona mapa pokazuje zależności tylko dla pomyślnie sbudowaną kodu. Jeśli wystąpią błędy kompilacji dla niektórych składników, te błędy pojawią się na mapie. Przed podjęciem decyzji dotyczących architektury na podstawie mapy upewnij się, że składnik jest w rzeczywistości skompilowany i ma od niego zależności.
