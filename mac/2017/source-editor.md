---
title: Edytor źródeł
description: Korzystanie z edytora źródłowego w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 187805767e9f67851975dccf8513c708c4233ccc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985217"
---
# <a name="source-editor"></a>Edytor źródeł

Niezawodny edytor źródłowy jest niezbędny do pisania kodu w sposób zwięzły i wydajny. Visual Studio dla komputerów Mac udostępnia zaawansowany edytor źródłowy, który znajduje się w centrum interakcji z IDE. Edytor źródeł udostępnia funkcje, których można oczekiwać i które trzeba wykonać swoją pracę z łatwością: Od podstaw, takich jak podświetlanie składni, fragmenty kodu i składanie kodu, po zalety integracji kompilatora Roslyn, takie jak w pełni funkcjonalny kod IntelliSense Zakończenia.

Edytor źródłowy w programie Visual Studio dla komputerów Mac umożliwia bezproblemowe środowisko ze wszystkimi innymi funkcjami w IDE, takimi jak debugowanie, refaktoryzowanie i integracja kontroli wersji.

W tym artykule przedstawiono niektóre z kluczowych funkcji edytora źródłowego i bada, jak można używać programu Visual Studio dla komputerów Mac, aby być jak najbardziej produktywne.

## <a name="the-source-editor-experience"></a>Środowisko edytora źródeł

Efektywne przeglądanie i przenoszenie w całym kodzie jest integralną częścią przepływu pracy deweloperskiego. Dokładnie, jak zdecydujesz się wyświetlić i utrzymać kod jest osobista decyzja, która różni się między deweloperami — i często między projektami.

Visual Studio dla komputerów Mac oferuje wiele zaawansowanych funkcji, aby tworzenie między platformami tak dostępne i jak najbardziej przydatne. W poniższych sekcjach opisano niektóre z najważniejszych wydarzeń.

## <a name="code-folding"></a>Składanie kodu

Składanie kodu ułatwia zarządzanie plikami kodu źródłowego, umożliwiając deweloperom wyświetlanie lub ukrywanie pełnych sekcji kodu, takich jak używanie dyrektyw, kodu i komentarzy oraz #region instrukcji. Składanie kodu jest domyślnie wyłączone w programie Visual Studio dla komputerów Mac

Aby włączyć składanie kodu, przejdź do **programu Visual Studio > Preferencje > Edytor tekstu > Ogólne > składane kodu:**

![Opcje składania kodu](media/source-editor-image1.png)

To menu zawiera również opcję składania #regions i komentarzy domyślnie, wyświetlając nazwaną wskazówkę zamiast kodu.

Aby wyświetlić lub ukryć sekcje, użyj widżetu ujawnienia obok numeru wiersza:

![Pokazywanie lub ukrywanie sekcji w kodzie](media/source-editor-image2.png)

Można również przełączać się między pokazywaniem i ukrywaniem zagęszków za pomocą elementu menu **Widok > Składany > Przełączanie składania / Przełączanie wszystkich zagięć:**

![Element menu składanego](media/source-editor-image19.png)

Ten element menu może być również używany do włączania lub wyłączania składania kodu.

## <a name="white-space"></a>Odstępu

Może być konieczne wyświetlenie niewidocznych znaków w kodzie źródłowym. Jest to widoczny sposób, aby upewnić się, że przestrzegasz standardów kodowania i nie niepotrzebnie tracisz miejsce. Jest to również przydatne podczas pisania F#, który zależy od dokładnie wcięte wiersze do oceny kodu.

Ustaw opcje pokazywania odstępów, przechodząc do **programu Visual Studio > preferencje > Edytor tekstu > znaczniki i linijki**. Wybranie tej opcji umożliwia _ustawienie, kiedy_ będą wyświetlane niewidoczne znaki: Nigdy, Przy zaznaczeniu lub Zawsze:

![Pokaż opcje niewidzialnych znaków](media/source-editor-image3.png)

Dostępna jest również opcja pokazywania kart, spacji i zakończeń linii:

![Pokazywalki i spacje](media/source-editor-image4.png)

Niewidoczne znaki są wyświetlane jako szare kropki, jak pokazano na poniższej ilustracji:

![wyświetlana przestrzeń](media/source-editor-image22.png)

## <a name="ruler"></a>Linijki

Linijka kolumny jest przydatna do określania długości linii, szczególnie podczas pracy z zespołem, który ma wytyczne dotyczące długości linii. Linijkę kolumny można włączyć lub wyłączyć, przechodząc do **programu Visual Studio > Preferencje > Edytor tekstu > znaczniki i linijki** oraz wybierając (lub odznaczając) Pokaż **linijkę kolumny,** jak pokazano na poniższej ilustracji:

![Okno dialogowe Preferencje z wyróżnioną "pokaż linijkę kolumny"](media/source-editor-image5.png)

 Jest to wyświetlana w edytorze źródłowym jako pionowa jasnoszary.

## <a name="highlight-identifier-references"></a>Wyróżnianie odwołań do identyfikatorów

Dzięki włączeniu opcji "Wyróżnij odwołania do identyfikatorów" można wybrać dowolny symbol w kodzie źródłowym, a edytor źródłowy zapewni wizualny przewodnik po wszystkich innych odwołaniach w tym pliku. Aby włączyć tę opcję, przejdź do **programu Visual Studio > Preferencje > Edytor tekstu > znaczniki i linijki** i wybierz pozycję _Wyróżnij odniesienia do identyfikatorów_, jak pokazano na poniższej ilustracji:

![Okno dialogowe Preferencje z wyróżnionym "Wyróżnij odniesienia do identyfikatorów"](media/source-editor-image6.png)

Kolor podświetlenia jest również przydatny do oznaczania, że coś jest przypisywane lub odwołujące się do niego. Jeśli coś jest przypisane, jest podświetlony na czerwono; jeśli odwołuje się do niego, jest podświetlony na niebiesko:

![przykład przedstawiający kolor podświetlenia](media/source-editor-image7.png)

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu (Visual Studio w systemie Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Tworzenie nakreślenia (Visual Studio w systemie Windows)](/visualstudio/ide/outlining)