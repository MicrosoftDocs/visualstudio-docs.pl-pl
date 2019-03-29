---
title: Edytor źródła
description: Za pomocą edytora źródła w programie Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: b284cde511b17863861908d9967bbea7672e297b
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58573067"
---
# <a name="source-editor"></a>Edytor źródła

Edytor wiarygodnego źródła ma zasadnicze znaczenie dla pisania kodu, zwięzły i wydajne. Program Visual Studio dla komputerów Mac udostępnia edytora zaawansowanego źródła, który znajduje się w środku interakcje ze środowiskiem IDE programu. Edytor źródła zawiera funkcje, które mogą spodziewać się i potrzebują do wykonania swojej pracy z łatwością: Od podstawowych takich wyróżniania składni, fragmenty kodu i składanie kodu, aby korzyści z integracji kompilator Roslyn, takie jak IntelliSense w pełni funkcjonalne uzupełnianie kodu.

Edytor źródła w programie Visual Studio dla komputerów Mac umożliwia bezproblemowe środowisko z wszystkimi funkcjami w środowisku IDE, takie jak debugowania, refaktoryzacji i integrację kontroli wersji.

W tym artykule przedstawiono niektóre najważniejsze funkcje Edytor źródła i analizuje, jak można użyć programu Visual Studio dla komputerów Mac na taką samą produktywność jak to możliwe.

## <a name="the-source-editor-experience"></a>Środowisko Edytor źródła

Wyświetlanie i wydajnego przenoszenia w całym kodzie jest integralną częścią przepływu pracy tworzenia oprogramowania. Dokładnie decyzja dotycząca wyświetlanie i utrzymanie kodu jest osobiste decyzji, które różni się od deweloperów — i często między projektami.

Program Visual Studio for Mac oferuje wiele zaawansowanych funkcji dzięki niej programowanie dla wielu platform oraz dostępne jako użyteczne, jak to możliwe. W następujących sekcjach opisano niektóre najważniejsze funkcje.

## <a name="code-folding"></a>Składanie kodu

Składanie kodu ułatwia zarządzanie plikami kodu źródłowego w dużych, umożliwiając deweloperom Pokaż lub Ukryj zakończenie sekcji kodu, takich jak przy użyciu dyrektyw, standardowy kod i komentarze i instrukcje #region. Składanie kodu jest domyślnie wyłączona w programie Visual Studio dla komputerów Mac

Aby włączyć zwijanie kodu, przejdź do **programu Visual Studio > Preferencje > Edytor tekstu > Ogólne > składanie kodu**:

![Opcje składanie kodu](media/source-editor-image1.png)

To menu umożliwia także opcji, aby złożyć #regions i komentarze domyślnie wyświetlania o nazwie wskazówki, zamiast kodu.

Aby pokazać lub ukryć sekcje, należy użyć widget ujawniania obok numer wiersza:

![Pokazywanie lub ukrywanie sekcji w kodzie](media/source-editor-image2.png)

Możesz także przełączać się między pokazywaniu i ukrywaniu złożeń przy użyciu **Widok > Zwijanie > składania przełącznik / Przełącz wszystkie złożeń** element menu:

![Zwijanie elementu Menu.](media/source-editor-image19.png)

Ten element menu można również włączyć lub wyłączyć składanie kodu.

## <a name="white-space"></a>Biały znak

Może być konieczne w celu wyświetlania niewidoczne znaki w kodzie źródłowym. Jest widoczny sposób, aby upewnić się, że one być przestrzega standardy kodowania i nie niepotrzebnie Marnowanie miejsca. Jest to również przydatne podczas pisania F#, która jest zależna od dokładnie w pozycji wcięcia wierszy dla oceny kodu.

Ustawianie opcji, aby wyświetlić białe znaki, przechodząc do **programu Visual Studio > Preferencje > Edytor tekstu > Znaczniki i linijki**. Wybranie tej opcji umożliwia ustawienie _podczas_ będą wyświetlane niewidoczne znaki: Nie, na wybór lub zawsze:

![Pokaż opcje niewidoczne znaki](media/source-editor-image3.png)

Opcję, aby wyświetlać karty, spacje i końce wierszy jest również dostępna:

![Pokaż znaki tabulacji i spacje](media/source-editor-image4.png)

Niewidoczne znaki są wyświetlane jako szary kropki, jak pokazano na poniższej ilustracji:

![wyświetlane białe znaki](media/source-editor-image22.png)

## <a name="ruler"></a>Linijki

Linijka kolumny jest przydatne do określania długości wiersza, szczególnie w przypadku, gdy pracuje zespół, który zawiera wytyczne dotyczące długość wiersza. Linijkę kolumn można włączyć lub wyłączyć, przechodząc do **programu Visual Studio > Preferencje > Edytor tekstu > Znaczniki i linijki** i wybranie (lub usunięcie zaznaczenia tej opcji) **linijkę kolumn pokazują**, jak pokazano w poniższej ilustracji:

![Okno dialogowe preferencji przy użyciu "Pokaż linijkę kolumn" wyróżniony](media/source-editor-image5.png)

 Spowoduje to wyświetlenie jako Jasny pionowy szara linia w edytorze źródła.

## <a name="highlight-identifier-references"></a>Wyróżnij odwołania do identyfikatorów

Za pomocą "Wyróżnij odwołania do identyfikatorów" opcja jest włączona możesz wybrać dowolny symbol w kodzie źródłowym, a Edytor źródła zapewni przewodnik wizualny po wszystkie odwołania w tym pliku. Aby włączyć tę opcję, przejdź do **programu Visual Studio > Preferencje > Edytor tekstu > Znaczniki i linijki** i wybierz _wyróżniać odwołania do identyfikatorów_, jak pokazano na poniższej ilustracji:

![Okno dialogowe preferencji przy użyciu "Wyróżnij odwołania do identyfikatorów" wyróżniony](media/source-editor-image6.png)

Kolor wyróżnienia jest również przydatne w przypadku określania to coś jest przypisywany lub odwołania. Jeśli coś, co jest przypisane, jest wyróżniony na czerwono; jest ona przywoływana jest wyróżniany kolorem niebieskim:

![przykład przedstawiający kolor wyróżnienia](media/source-editor-image7.png)

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu (Visual Studio Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Konspekt (Visual Studio Windows)](/visualstudio/ide/outlining)