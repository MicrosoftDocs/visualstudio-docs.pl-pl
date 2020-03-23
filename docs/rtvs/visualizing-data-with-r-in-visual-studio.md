---
title: Wizualizacja danych za pomocą języka R
description: Jak wykreślić dane z programów języka R w programie Visual Studio przy użyciu okien wydruku.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: a48ad7800f8ea2b992e848cfbf6b4fdac99b2062
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62811189"
---
# <a name="create-visual-data-plots-with-r"></a>Tworzenie wykresów danych wizualnych za pomocą języka R

Kreślenie jest kluczową częścią przepływu pracy analityka danych. W programie R Tools for Visual Studio (RTVS) wszystkie centra aktywności kreślenia wokół jednego lub więcej okien wydruku, które mają na celu zwiększenie wydajności dzięki temu kluczowemu działaniu.

![Kreślenie obrazu bohatera](media/plotting-hero-image.png)

|   |   |
|---|---|
| ![ikona kamery filmowa dla wideo](../install/media/video-icon.png "Obejrzyj film") | [Obejrzyj film (youtube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) na temat drukowania z R (2m 02s). |

## <a name="the-plot-window"></a>Okno wydruku

Okno wydruku zawiera serię wykresów, w których `plot` każdy wykres jest generowany przez polecenie. Na przykład `plot(1:100)` użycie powoduje utworzenie nowego okna wydruku, jeśli nie jest jeszcze dostępne:

![1 do 100 Wykres liniowy](media/plotting-1-to-100.png)

Technicznie rzecz biorąc, `plot` polecenia R renderują swoje dane wyjściowe na urządzeniu graficznym R; okno wydruku renderuje zawartość urządzenia graficznego R, dlatego każde okno wydruku otrzymuje numer urządzenia.

Okna wydruku są niezależne od projektów programu Visual Studio i pozostają otwarte podczas ładowania i zamykania projektów.

Generowanie wykresu wykorzystuje okno "aktywnego" wykresu, zapisując poprzednią fabułę historii wydruku (patrz [Historia wydruku).](#plot-history) Na przykład `plot(100:1)` wprowadź, a pierwszy wykres zostanie zastąpiony linią w dół.

Podobnie jak wszystkie inne okna programu Visual Studio. okno wydruku obsługuje niestandardowe układy (zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Okna wydruku mogą być zadokowane w różnych lokalizacjach w ramce programu Visual Studio, zmiany rozmiaru w tej ramce lub wyciągnięte z ramki całkowicie w celu niezależnej zmiany rozmiaru.

Zmiana rozmiaru okna wydruku zawsze powoduje ponowne renderowanie wykresu w celu zapewnienia najlepszej jakości obrazu. Zazwyczaj chcesz zmienić rozmiar wykresu przed wyeksportowaniem wykresu do pliku lub do schowka za pomocą poleceń opisanych w następnej sekcji.

## <a name="plot-window-commands"></a>Polecenia okna wydruku

Pasek narzędzi okna wydruku zawiera odpowiednie polecenia, z których większość jest również dostępna za pośrednictwem menu **R Tools** > **Plots.**

| Button | Polecenie | Opis |
| --- | --- | --- |
| ![Przycisk Okna nowego wydruku](media/plotting-toolbar-01-new-plot-window.png) | Nowe okno działki | Tworzy oddzielne okno wydruku z własną historią. Zobacz [Wiele okien wydruku](#multiple-plot-windows). |
| ![Przycisk Uaktywnianie okna wydruku](media/plotting-toolbar-02-activate-plot-window.png) | Aktywowanie okna wydruku | Ustawia bieżące okno wydruku jako aktywne `plot` okno, tak aby kolejne polecenia były renderowane w tym oknie. Zobacz [Wiele okien wydruku](#multiple-plot-windows). Zobacz [Wiele okien wydruku](#multiple-plot-windows). |
| ![Przycisk okna historii kreślenia](media/plotting-toolbar-03-plot-history.png) | Okno Historia wydruku | Otwiera okno ze wszystkimi wykresami w historii wyświetlanymi jako miniatury. Zobacz [Historia wydruku](#plot-history). |
| ![Wykreślanie przycisków historii](media/plotting-toolbar-04-plot-history-arrows.png) | Poprzednia/następna działka |  Przechodzi do poprzedniego lub następnego wykresu w historii. Historię można również nawigować za pomocą klawiszy Ctrl+Alt+F11 (Poprzedni) i Ctrl+Alt+F12 (Dalej). Zobacz [Historia wydruku](#plot-history). |
| ![Przycisk Zapisz jako obraz](media/plotting-toolbar-05-save-as-image.png)| Zapisz jako obraz | Monituje o podanie nazwy pliku i zapisuje bieżący wykres (zawartość okna, w rozmiarze okna) w pliku obrazu. Dostępne formaty `.png` `.jpg`to `.bmp`, `.tif`, i . |
| ![Przycisk Zapisz jako PDF](media/plotting-toolbar-06-save-as-pdf.png)| Zapisz w formacie PDF | Zapisuje bieżący wykres w pliku PDF przy użyciu bieżącego rozmiaru okna. Wykres zostanie ponownie renderowany, jeśli plik PDF jest skalowany. |
| ![Przycisk Kopiuj jako bitmapę](media/plotting-toolbar-07-copy-as-bitmap.png)| Kopiowanie jako mapa bitowa | Kopiuje wykres do schowka jako mapę bitową rastrową przy użyciu bieżącego rozmiaru okna. |
| ![Przycisk Kopiuj jako metaplik](media/plotting-toolbar-08-copy-as-metafile.png)| Kopiuj jako metaplik | Kopiuje wykres do schowka jako [metaplik systemu Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). |
| ![Przycisk Usuń wydruk](media/plotting-toolbar-09-remove-plot.png)| Usuń wykres | Usuwa bieżący wykres z historii. |
| ![Przycisk Wyczyść wszystkie wykresy](media/plotting-toolbar-10-clear-all-plots.png) | Wyczyść wszystkie wykresy | Usuwa wszystkie wykresy z historii (monituje o potwierdzenie). |

## <a name="multiple-plot-windows"></a>Wiele okien wydruku

Ponieważ analitycy danych często pracują z wieloma wykresami z wielu różnych zestawów danych, RTVS umożliwia tworzenie jak największej liczby niezależnych okien wydruku. Następnie można rozmieścić te okna, jak chcesz w ramce programu Visual Studio lub poza ramką całkowicie. (Zobacz [Dostosowywanie układów okien w programie Visual Studio,](../ide/customizing-window-layouts-in-visual-studio.md) aby uzyskać ogólne informacje na temat dokowania i zmiany rozmiaru okien).

Nowe okno wydruku można utworzyć za pomocą przycisku paska narzędzi lub **R Narzędzia** > **Wykresy** > **Nowe okno wydruku**. Nowe okno wydruku staje się *aktywnym* oknem, w którym renderowane są nowe wykresy. Aby zmienić aktywne okno, przełącz się do niego i wybierz przycisku **Aktywuj okno wydruku** lub **R Narzędzia** > **Wykresy** > **Aktywuj okno kreślenia**.

Wykresy są również niezależnymi obiektami, co oznacza, że można je kopiować lub przenosić między oknami wydruku za pomocą przeciągania i upuszczania za pomocą myszy lub za pomocą poleceń **Kopiuj**, **Wytnij**i Wklej w **kontekście** i **menu Edycja.**

Domyślnym zachowaniem przeciągania i upuszczania jest kopiowanie; , aby przenieść, przeciągnij i upuść, przytrzymując klawisz **Shift.**

## <a name="plot-history"></a>Historia wydruku

Polecenia wydruku są zachowywane w historii wydruku dla każdego okna, zapewniając zachowanie wszystkich kreśleń w ramach sesji. Aby poruszać się po historii, użyj przycisków strzałek na pasku narzędzi okna wydruku lub **Ctrl**+**Alt**+**F11** i **Ctrl**+**Alt**+**F12**. Można również ponownie usunąć pojedyncze wykresy lub wyczyścić wszystkie wykresy z okna za pomocą przycisków paska narzędzi lub poleceń menu **R Tools** > **Plots.**

Aby wyświetlić całą kolekcję wykresów, otwórz okno historii wydruku za pomocą przycisku paska narzędzi lub **R Tools** > **Plots Plots** > **History Window**.
Historia zawiera listę miniatur wykresów, które zostały wyświetlone w tym oknie, pogrupowanych według różnych okien wydruku (lub urządzeń). Za pomocą przycisków powiększenia na pasku narzędzi zmienia się rozmiar miniatur.

![Okno Historia wydruku](media/plotting-plot-history-window.png)

Aby otworzyć wykres w skojarzonym oknie, kliknij dwukrotnie ten wykres, zaznacz go, a następnie wybierz przycisk **Pokaż pasek** narzędzi Wykres lub kliknij prawym przyciskiem myszy i wybierz polecenie **Pokaż wykres**. Można również wybrać pojedynczy wykres i skopiować, wyciąć lub usunąć z kontekstu i **menu edycji.**

Okres istnienia historii wydruku we wszystkich oknach jest powiązany z okresem istnienia interaktywnej sesji języka R. Jeśli zresetujesz sesję języka R lub zakończysz i uruchomisz ponownie program Visual Studio, historia wydruku zostanie zresetowana.

## <a name="programmatically-manipulate-plot-windows"></a>Programowo manipuluj oknami wydruku

Można programowo manipulować oknami wydruku z kodu R, używając numerów urządzeń do identyfikowania określonych okien wydruku.

- `dev.list()`: Lista wszystkich urządzeń graficznych w ramach bieżącej sesji R.
- `dev.new()`: Utwórz nowe urządzenie graficzne (nowe okno wydruku).
- `dev.set(<device number>)`: Ustaw aktywne urządzenie graficzne.
- `dev.off()`: Usuń aktywne urządzenie.
