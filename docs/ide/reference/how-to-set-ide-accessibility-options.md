---
title: 'Instrukcje: Ustawianie opcji ułatwień dostępu IDE'
description: Dowiedz się, jak ustawić opcje ułatwień dostępu w programie Visual Studio, które ułatwią wszystkim korzystanie z zintegrowanego środowiska programistycznego (IDE), w tym dla osób, które mają niewielki dostęp do odczytu i dla osób, które mają ograniczoną ruch.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d7cc99747571feb5b443f10355d867da7c22f44
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952918"
---
# <a name="how-to-set-ide-accessibility-options"></a>Instrukcje: Ustawianie opcji ułatwień dostępu IDE

Program Visual Studio zawiera funkcje, które ułatwiają osobom, które mają niewielki dostęp do odczytu i dla osób, które mają ograniczoną ruch. Na przykład można zmienić rozmiar i kolor tekstu w edytorach, zmienić rozmiar tekstu i przycisków na paskach narzędzi i zmienić ustawienia, aby pomóc w ukończeniu funkcji lub instrukcji.

Ponadto program Visual Studio obsługuje układy klawiatury Dvoraka, co sprawia, że najczęściej wpisywane znaki są bardziej dostępne. Można również dostosować domyślne skróty klawiaturowe dostępne w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od opisanych tutaj, które mogą się różnić w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Aby dowiedzieć się więcej o najnowszych aktualizacjach dostępności, zobacz wpis w blogu dotyczący [ulepszeń ułatwień dostępu w programie Visual Studio 2017 w wersji 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) .

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Edytory, okna dialogowe i okna narzędzi

Domyślnie okna dialogowe i okna narzędzi w programie Visual Studio używają tego samego rozmiaru i koloru czcionki co system operacyjny. Ustawienia koloru dla ramki środowiska IDE, okien dialogowych, pasków narzędzi i okien narzędzi są oparte na schemacie kolorów: jasne lub ciemne. Bieżący motyw kolorów można zmienić w [oknie dialogowym Opcje: środowisko > ogólne](../../ide/reference/general-environment-options-dialog-box.md).

Okna podręczne można także wyświetlić w widoku Kod edytora. Te okna mogą monitować o dostępne elementy członkowskie bieżącego obiektu i parametry, aby ukończyć funkcję lub instrukcję. Te okna mogą być przydatne, jeśli masz problemy z wpisywaniem. Jednak zakłócają one fokus w edytorze kodu, co może być problematyczne dla niektórych użytkowników.

Oto jak wyłączyć okna podręczne:

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

1. Wybierz kolejno pozycje **Edytor tekstu**  >  **wszystkie języki**  >  **Ogólne**.

1. Wyczyść pola wyboru **listy członków** i **informacji o parametrach** .

Możesz zmienić rozmieszczenie systemu Windows w zintegrowanym środowisku programistycznym (IDE), aby najlepiej dopasować się do pracy. Każde okno narzędzi można zadokować, przepływać, ukryć lub automatycznie ukryć. Aby uzyskać więcej informacji na temat zmiany układów okien, zobacz [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Zmienianie rozmiaru tekstu

Możesz zmienić ustawienia okien narzędzi tekstowych, takich jak okno **polecenia** , okno **bezpośrednie** i okno **dane wyjściowe** , używając opcji **Narzędzia**  >    >    >  **czcionki i kolory** środowiska.

Po wybraniu opcji **[wszystkie okna narzędzi tekstowych]** na liście rozwijanej **Pokaż ustawienia dla** , ustawienie domyślne zostanie wyświetlone na liście rozwijanej na **pierwszym planie elementu** **i w** **tle elementu** . Wybierz przycisk **niestandardowy** , aby zmienić te ustawienia.

Możesz również zmienić ustawienia wyświetlania tekstu w edytorze. Oto jak to zrobić.

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

1. Wybierz czcionki **środowiskowe**  >  **i kolory**.

1. Wybierz opcję z menu rozwijanego **Pokaż ustawienia dla** .

    Aby zmienić rozmiar czcionki dla tekstu w edytorze, wybierz **Edytor tekstu**.

    Aby zmienić rozmiar czcionki dla tekstu w oknach narzędzi tekstowych, wybierz opcję **[wszystkie okna narzędzi tekstowych]**.

    Aby zmienić rozmiar czcionki dla tekstu etykietki narzędzia w edytorze, wybierz **etykietkę narzędzia edytora**.

    Aby zmienić rozmiar czcionki dla tekstu w okienkach wyskakujących uzupełniania instrukcji, wybierz opcję **uzupełnianie instrukcji**.

1. Z **elementów wyświetlanych** wybierz opcję **zwykły tekst**.

1. W polu **czcionka** wybierz nowy typ czcionki.

1. W polu **rozmiar** wybierz nowy rozmiar czcionki.

    > [!TIP]
    > Aby zresetować rozmiar tekstu dla okien narzędzi tekstowych i edytorów, wybierz opcję **Użyj wartości domyślnych**.

7. Wybierz przycisk **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Zmień kolory używane w środowisku IDE

Można zmienić domyślne kolory tekstu, wskaźników marginesów, odstępu i elementów kodu w edytorze. Oto jak to zrobić.

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

1. W folderze **środowisko** wybierz pozycję **czcionki i kolory**.

1. W obszarze **Pokaż ustawienia dla** wybierz **Edytor tekstu**.

1. Z **elementów wyświetlanych** wybierz element, którego ekran należy zmienić, na przykład **zwykły tekst**, **margines wskaźnika**, **widoczny odstęp**, **nazwa atrybutu HTML** lub **atrybut XML**.

1. Wybierz pozycję Ustawienia wyświetlania z następujących opcji: **pierwszy plan elementu**, **tło elementu** i **pogrubienie**.

1. Wybierz przycisk **OK**.

> [!TIP]
> Aby użyć kolorów o dużym kontraście dla wszystkich okien aplikacji w systemie operacyjnym, naciśnij klawisz **lewy Alt** w + **lewo przesuń** klawisz + **PrtScn**. Jeśli program Visual Studio jest otwarty, Zamknij, a następnie otwórz go ponownie, aby w pełni zaimplementować kolory o wysokim kontraście.

## <a name="toolbars"></a>Paski narzędzi

Aby poprawić użyteczność i dostępność paska narzędzi, możesz dodać tekst do przycisków paska narzędzi.

### <a name="to-assign-text-to-toolbar-buttons"></a>Aby przypisać tekst do przycisków paska narzędzi

1. W menu **Narzędzia** wybierz polecenie **Dostosuj**.

1. W oknie dialogowym **Dostosowywanie** wybierz kartę **polecenia** .

1. Wybierz pozycję **pasek narzędzi**, a następnie wybierz nazwę paska narzędzi zawierającego przycisk, dla którego ma być wyświetlany tekst.

1. Z listy wybierz polecenie, które ma zostać zmienione.

1. Wybierz **Modyfikuj zaznaczenie**.

1. Wybierz **obraz i tekst**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Aby zmodyfikować wyświetlany tekst na przycisku

1. Wybierz pozycję **Modyfikuj zaznaczenie**.

1. Obok **nazwy** w polu Wstaw Podaj nowy podpis dla wybranego przycisku.

## <a name="see-also"></a>Zobacz też

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Ułatwienia dostępu dla Visual Studio dla komputerów Mac](/visualstudio/mac/accessibility/)
* [Zasoby do projektowania dostępnych aplikacji](../../ide/reference/resources-for-designing-accessible-applications.md)
