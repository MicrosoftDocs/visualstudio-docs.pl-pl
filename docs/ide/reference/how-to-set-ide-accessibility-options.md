---
title: 'Jak: Ustawianie opcji ułatwień dostępu IDE'
description: Dowiedz się, jak ustawić opcje ułatwień dostępu w programie Visual Studio, które ułatwi korzystanie z zintegrowanego środowiska programistycznego (IDE), w tym dla osób o słabym wzroku do odczytu i dla osób o ograniczonej zręczności do pisania.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63bba4e8defcd727f05dbc209aa2f48f7d5f2c92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "70107787"
---
# <a name="how-to-set-ide-accessibility-options"></a>Jak: Ustawianie opcji ułatwień dostępu IDE

Visual Studio zawiera funkcje, które ułatwiają dla osób, które mają niedowidzących do odczytu i dla osób, które mają ograniczoną zręczność do pisania. Można na przykład zmienić rozmiar i kolor tekstu w edytorach, zmienić rozmiar tekstu i przycisków na paskach narzędzi oraz zmienić ustawienia, aby ułatwić ukończenie funkcji lub instrukcji.

Ponadto visual studio obsługuje układy klawiatury Dvorak, które sprawiają, że najczęściej wpisywane znaki są bardziej dostępne. Można również dostosować domyślne skróty klawiaturowe dostępne w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Okna dialogowe i polecenia menu mogą różnić się od opisanych w tym miejscu, co może się różnić w zależności od aktywnych ustawień lub wersji. Aby zmienić ustawienia, wybierz polecenie **Importuj i eksportuj ustawienia** w menu **Narzędzia.** Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Aby dowiedzieć się więcej o najnowszych aktualizacjach ułatwień dostępu, zobacz wpis w blogu [dotyczące ułatwień dostępu w programie Visual Studio 2017 w wersji 15.3.](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/)

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Edytory, okna dialogowe i okna narzędzi

Domyślnie okna dialogowe i okna narzędzi w programie Visual Studio używają tego samego rozmiaru czcionki i kolorów co system operacyjny. Ustawienia kolorów ramki IDE, okien dialogowych, pasków narzędzi i okien narzędzi są oparte na schemacie kolorów: jasnym lub ciemnym. Bieżący motyw kolorów można zmienić w [oknie dialogowym Opcje: Środowisko > Ogólne](../../ide/reference/general-environment-options-dialog-box.md).

W widoku Kod edytora można również wyświetlić okna podręczne. Te okna mogą monitować o dostępnych członków na bieżący obiekt i parametry, aby zakończyć funkcję lub instrukcję. Te okna mogą być pomocne, jeśli masz trudności z pisaniem. Jednak kolidują one z fokusem w edytorze kodu, co może być problematyczne dla niektórych użytkowników.

Aby wyłączyć wyskakujące okienka:

1. Z menu **Narzędzia** wybierz polecenie **Opcje**.

1. Wybierz **edytor** > tekstu**Wszystkie języki** > **ogólne**.

1. Wyczyść pola wyboru **Automatyczne elementy członkowskie listy** i informacje o **parametrach.**

Okna można zmienić w zintegrowanym środowisku programistycznym (IDE), aby jak najlepiej dopasować je do sposobu pracy. Można dokować, unosić się, ukrywać lub automatycznie ukrywać każde okno narzędzia. Aby uzyskać więcej informacji na temat zmieniania układów okien, zobacz [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Zmienianie rozmiaru tekstu

**Options** > **Environment** > Ustawienia okien narzędzi tekstowych, takich jak okno **Polecenia,** **Okno Natychmiastowe** i **Dane wyjściowe,** można zmienić za pomocą **opcji Narzędzia** > **Czcionki środowiska i kolory**.

Po **wybraniu opcji [Narzędzie tekstu Windows]** na liście rozwijanej **Pokaż ustawienia** dla wyświetleń ustawienie domyślne jest wyświetlane jako **domyślne** **na listach** rozwijanych Element pierwszego planu i **W tle elementu.** Wybierz przycisk **Niestandardowy,** aby zmienić te ustawienia.

Można również zmienić ustawienia sposobu wyświetlania tekstu w edytorze. Oto jak to zrobić.

1. Z menu **Narzędzia** wybierz polecenie **Opcje**.

1. Wybierz**czcionki i kolory** **środowiska** > .

1. Wybierz opcję z menu rozwijanego **Pokaż ustawienia** dla.

    Aby zmienić rozmiar czcionki tekstu w edytorze, wybierz pozycję **Edytor tekstu**.

    Aby zmienić rozmiar czcionki tekstu w oknach narzędzi tekstowych, wybierz opcję **[Wszystkie narzędzia tekstowe Windows]**.

    Aby zmienić rozmiar czcionki tekstu etykietki narzędziowej w edytorze, wybierz pozycję **Etykietka narzędzia edytora**.

    Aby zmienić rozmiar czcionki dla tekstu w wyskakujących okienkach uzupełniania instrukcji, wybierz opcję **Uzupełnianie instrukcji**.

1. W **obszarze Elementy wyświetlane**wybierz pozycję Zwykły **tekst**.

1. W **polu Czcionka**wybierz nowy typ czcionki.

1. W **polu Rozmiar**wybierz nowy rozmiar czcionki.

    > [!TIP]
    > Aby zresetować rozmiar tekstu dla okien i edytorów narzędzi tekstowych, wybierz pozycję **Użyj ustawień domyślnych**.

7. Wybierz pozycję **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Zmienianie kolorów używanych w ide

Można zmienić domyślne kolory tekstu, wskaźników marginesu, odstępu i elementów kodu w edytorze. Oto jak to zrobić.

1. Z menu **Narzędzia** wybierz polecenie **Opcje**.

1. W folderze **Środowisko** wybierz pozycję **Czcionki i kolory**.

1. W **obszarze Pokaż ustawienia dla**pozycji , wybierz pozycję Edytor **tekstu**.

1. W **obszarze Elementy wyświetlane**wybierz element, którego wyświetlanie należy zmienić, na przykład zwykły **tekst,** **margines wskaźnika,** **widoczny biały znak,** **nazwa atrybutu HTML**lub atrybut **XML**.

1. Wybierz ustawienia wyświetlania z następujących opcji: **Pierwszy plan elementu,** **Tło elementu**i **Pogrubienie**.

1. Wybierz pozycję **OK**.

> [!TIP]
> Aby użyć kolorów o wysokim kontraście dla wszystkich okien aplikacji w systemie operacyjnym, naciśnij **klawisz Left Alt**+**Left Shift**+**PrtScn**. Jeśli program Visual Studio jest otwarty, zamknij go, a następnie ponownie otwórz go, aby w pełni zaimplementować kolory o wysokim kontraście.

## <a name="toolbars"></a>Paski narzędzi

Aby poprawić użyteczność i dostępność paska narzędzi, można dodać tekst do przycisków paska narzędzi.

### <a name="to-assign-text-to-toolbar-buttons"></a>Aby przypisać tekst do przycisków paska narzędzi

1. Z menu **Narzędzia** wybierz polecenie **Dostosuj**.

1. W oknie dialogowym **Dostosowywanie** wybierz kartę **Polecenia.**

1. Wybierz **pozycję Pasek narzędzi**, a następnie wybierz nazwę paska narzędzi zawierającą przycisk, dla którego chcesz wyświetlić tekst.

1. Na liście wybierz polecenie, które chcesz zmienić.

1. Wybierz **pozycję Modyfikuj zaznaczenie**.

1. Wybierz **pozycję Obraz i tekst**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Aby zmodyfikować wyświetlany tekst w przycisku

1. Ponownie wybierz **opcję Modyfikuj zaznaczenie**.

1. Obok w **nazwie**wstawić, wstawić nowy podpis dla wybranego przycisku.

## <a name="see-also"></a>Zobacz też

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Ułatwienia dostępu dla programu Visual Studio dla komputerów Mac](/visualstudio/mac/accessibility/)
* [Zasoby do projektowania aplikacji dostępnych](../../ide/reference/resources-for-designing-accessible-applications.md)
