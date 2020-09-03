---
title: Edytor źródeł
description: Korzystanie z edytora źródła w Visual Studio dla komputerów Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: c4a22ec0765c39a8bec83f9e2acff7b22b706890
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173099"
---
# <a name="source-editor"></a>Edytor źródła

Niezawodny Edytor źródeł jest istotny do pisania kodu w zwięzły i wydajny sposób. Visual Studio dla komputerów Mac udostępnia zaawansowany edytor źródła, który jest w centrum interakcji z IDE. Edytor źródła udostępnia funkcje, które można oczekiwać i konieczność pracy z łatwością: od podstaw, takich jak wyróżnianie składni, fragmenty kodu i składanie kodu, do korzyści z integracji kompilatora Roslyn, takich jak w pełni funkcjonalne uzupełnianie kodu IntelliSense.

Edytor źródła w Visual Studio dla komputerów Mac umożliwia bezproblemowe środowisko pracy ze wszystkimi innymi funkcjami środowiska IDE, takimi jak debugowanie, refaktoryzacja i integracja kontroli wersji.

W tym artykule przedstawiono niektóre najważniejsze funkcje edytora źródła i przedstawiono sposób, w jaki można wykorzystać Visual Studio dla komputerów Mac, jak to możliwe.

## <a name="the-source-editor-experience"></a>Środowisko edytora źródła

Wydajne wyświetlanie i przechodzenie w całym kodzie jest integralną częścią przepływu pracy deweloperskiej. Dokładny sposób wyświetlania i konserwowania kodu jest indywidualną decyzją, która różni się między deweloperami i często między projektami.

Visual Studio dla komputerów Mac oferuje wiele zaawansowanych funkcji umożliwiających tworzenie aplikacji dla wielu platform jako dostępnych i przydatnych, jak to możliwe. W poniższych sekcjach opisano niektóre z nich.

## <a name="code-folding"></a>Składanie kodu

Łamanie kodu ułatwia zarządzanie dużymi plikami kodu źródłowego przez umożliwienie deweloperom wyświetlania lub ukrywania kompletnych części kodu, takich jak dyrektywy, kod standardowy i komentarze oraz instrukcje #region. Funkcja składania kodu jest domyślnie wyłączona w Visual Studio dla komputerów Mac

Aby włączyć funkcję składania kodu, przejdź do sekcji **preferencje > programu Visual Studio > Edytor tekstów > ogólne > składania kodu**:

![Opcje składania kodu](media/source-neweditor-image1.png)

To menu zawiera również opcję umieszczenia #regions i komentarzy domyślnie, wyświetlając wskazówkę o nazwie zamiast kodu.

Aby pokazać lub ukryć sekcje, użyj widżetu ujawniania obok numeru wiersza:

![Wyświetlanie lub ukrywanie sekcji w kodzie](media/source-neweditor-image2.png)

Możesz również przełączać się między pokazywaniem i ukrywaniem zagięć przy użyciu **widoku > składania > Przełącz pozycję zagnij/Przełącz wszystkie składowe** w menu:

![Element menu składania](media/source-editor-image19.png)

Ten element menu może być również używany do włączania lub wyłączania składania kodu.

## <a name="word-wrap"></a>Zawijanie wierszy

Zawijanie słów może pomóc w zarządzaniu miejscem podczas pracy nad długimi wierszami kodu lub z ograniczoną ilością widoku. Zawijanie wierszy może również upewnić się, że widok kodu zawiera pełną zawartość pliku źródłowego nawet podczas otwierania okienek, które mogą zasłaniać widok lub zmniejszyć szerokość widoku źródła. 

Zawijanie wyrazów jest domyślnie wyłączone, ale można je włączyć za pomocą **preferencji** w Visual Studio dla komputerów Mac. 

Aby włączyć zawijanie wierszy, przejdź do **> preferencji programu Visual Studio > edytorze tekstów > Zawijanie wierszy**:

![Opcje zawijania słów](media/source-neweditor-wordwrap1.png)

Po włączeniu zawijania wierszy wiersze, które przekraczają szerokość widoku edytora źródła, zostaną automatycznie zawinięte do następnego wiersza w pliku źródłowym. Możesz również włączyć opcję, która będzie wyświetlać widoczny symbol obok opakowanych wierszy. Pozwoli to na rozróżnienie wierszy, które zostały opakowane automatycznie, oraz tych, które zostały opakowane ręcznie.

![Opakowany tekst z włączonym zawijaniem wyrazów](media/source-neweditor-wordwrap2.png)

## <a name="ruler"></a>Podział

Linijka kolumn jest przydatna do określania długości linii, szczególnie podczas pracy nad zespołem, który ma wskazówki dotyczące długości linii. Linijki kolumn można włączać lub wyłączać, przechodząc do pozycji **preferencje > programu Visual Studio > edytorze tekstu > znaczniki i linijki** oraz wybierając (lub usuwając zaznaczenie) przycisk **Pokaż linijkę kolumn**, jak pokazano na poniższej ilustracji:

![Okno dialogowe preferencji z wyróżnioną pozycją "Pokaż linijkę kolumn"](media/source-editor-image5.png)

 Ten element jest wyświetlany jako pionowy, szary wiersz w edytorze źródła.

## <a name="highlight-identifier-references"></a>Wyróżnij odwołania do identyfikatorów

Po włączeniu opcji "odwołuje się do identyfikatora wyróżnienia" można wybrać dowolny symbol w kodzie źródłowym, a Edytor źródła udostępni przewodnik wizualny do wszystkich innych odwołań w tym pliku. Aby włączyć tę opcję, przejdź do **> preferencji programu Visual Studio > edytora tekstu > znaczniki i linijki** , a następnie wybierz pozycję _Wyróżnij odwołania do identyfikatora_, jak pokazano na poniższej ilustracji:

![Okno dialogowe preferencji z wyróżnionymi odwołaniami do identyfikatora wyróżnienia](media/source-editor-image6.png)

Kolor wyróżnienia jest również przydatny do oznaczania, że element jest przypisywany lub przywoływany. Jeśli coś jest przypisane, zostanie wyróżnione na czerwono. Jeśli istnieje odwołanie, zostanie wyróżnione kolorem niebieskim:

![przykład pokazujący kolor wyróżnienia](media/source-editor-image7.png)

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu (Visual Studio w systemie Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Tworzenie konspektu (Visual Studio w systemie Windows)](/visualstudio/ide/outlining)
