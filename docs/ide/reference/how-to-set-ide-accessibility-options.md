---
title: 'Instrukcje: Ustawianie opcji ułatwień dostępu środowiska IDE'
description: Dowiedz się, jak ustawić opcje ułatwień dostępu w programie Visual Studio, które ułatwią wszystkim korzystanie z zintegrowanego środowiska programistycznego (IDE), w tym dla osób, które mają niewielki dostęp do odczytu i dla osób, które mają ograniczoną ruch.
ms.date: 08/22/2017
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a0b5835333bf8cd41ab653108054e2d3dd4c73e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919282"
---
# <a name="how-to-set-ide-accessibility-options"></a>Instrukcje: Ustawianie opcji ułatwień dostępu środowiska IDE

> [!TIP]
> Aby dowiedzieć się więcej o najnowszych aktualizacjach dostępności, zobacz wpis w blogu dotyczący [ulepszeń ułatwień dostępu w programie Visual Studio 2017 w wersji 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) .

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zawiera funkcje, które ułatwiają osobom, które mają słabą wizję do odczytu i dla osób, które mają ograniczoną ruch. Te funkcje obejmują zmianę rozmiaru i koloru tekstu w edytorach, zmianę rozmiaru tekstu i przycisków na paskach narzędzi oraz Autouzupełnianie dla metod i parametrów, aby podać kilka nazw.

Dodatkowo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje układy klawiatury Dvoraka, które sprawiają, że najczęściej wpisywane znaki są bardziej dostępne. Można również dostosować domyślne klawisze skrótów dostępne w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../environment-settings.md#reset-settings).

## <a name="editors-dialogs-and-tool-windows"></a>Edytory, okna dialogowe i okna narzędzi

Domyślnie okna dialogowe i okna narzędzi w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używają tego samego rozmiaru i koloru czcionki co system operacyjny. Ustawienia koloru dla ramki środowiska IDE, okien dialogowych, pasków narzędzi i okien narzędzi są oparte na schemacie kolorów: jasne lub ciemne. Bieżący motyw kolorów można zmienić w [oknie dialogowym ogólne, środowisko, opcje](../../ide/reference/general-environment-options-dialog-box.md).

Okna podręczne można także wyświetlić w widoku Kod edytora. Te okna mogą monitować o dostępne elementy członkowskie bieżącego obiektu i parametry, aby ukończyć funkcję lub instrukcję. Te okna mogą być przydatne, jeśli masz problemy z wpisywaniem. Jednak zakłócają one fokus w edytorze kodu, co może być problematyczne dla niektórych użytkowników. Możesz wyłączyć te okna, otwierając okno dialogowe Opcje i czyszcząc **listę członków** i **Informacje o parametrach** w **edytorze tekstu**, **wszystkie języki**, **Ogólne** strony w oknie dialogowym **Opcje** .

Możesz zmienić rozmieszczenie systemu Windows w zintegrowanym środowisku programistycznym (IDE), aby najlepiej dopasować się do pracy. Każde okno narzędzi można zadokować, przepływać, ukryć lub automatycznie ukryć.

Aby uzyskać więcej informacji na temat zmiany układów okien, zobacz [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Zmiana rozmiaru tekstu

Można zmienić ustawienia okien narzędzi tekstowych, takich jak okno **polecenia** , okno **bezpośrednie** i okno **dane wyjściowe** , w okienku **czcionki i kolory** w opcjach **środowiska** w oknie dialogowym **Narzędzia** . Po wybraniu opcji **[wszystkie okna narzędzi tekstowych]** na liście rozwijanej **Pokaż ustawienia dla** , ustawienie domyślne zostanie wyświetlone na liście rozwijanej na **pierwszym planie elementu** i w **tle elementu** . Możesz również zmienić ustawienia wyświetlania tekstu w edytorze.

#### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Aby zmienić rozmiar tekstu w oknach narzędzi tekstowych i edytorach

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

2. Wybierz **czcionki i kolory** w folderze **Environment** .

3. Wybierz opcję z menu rozwijanego **Pokaż ustawienia dla** .

     Aby zmienić rozmiar czcionki dla tekstu w edytorze, wybierz **Edytor tekstu**.

     Aby zmienić rozmiar czcionki dla tekstu w oknach narzędzi tekstowych, wybierz opcję **[wszystkie okna narzędzi tekstowych]** .

     Aby zmienić rozmiar czcionki dla tekstu etykietki narzędzia w edytorze, wybierz **etykietkę narzędzia edytora**.

     Aby zmienić rozmiar czcionki dla tekstu w okienkach wyskakujących uzupełniania instrukcji, wybierz opcję **uzupełnianie instrukcji**.

4. Z **elementów wyświetlanych**wybierz opcję **zwykły tekst**.

5. W polu **czcionka**wybierz nowy typ czcionki.

6. W polu **rozmiar**wybierz nowy rozmiar czcionki.

    > [!NOTE]
    > Aby zresetować rozmiar tekstu dla okien narzędzi tekstowych i edytorów, wybierz opcję **Użyj wartości domyślnych**.

7. Wybierz **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Zmień kolory używane w środowisku IDE

Możesz również zmienić domyślne kolory tekstu, wskaźników marginesów, białego znaku i elementów kodu w edytorze.

> [!NOTE]
> Aby użyć kolorów o dużym kontraście dla wszystkich okien aplikacji w systemie operacyjnym, naciśnij klawisze z lewej <strong>Alt +</strong>Strzałka w lewo **Shift + Print Screen**. Jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest otwarte, Zamknij i Otwórz ponownie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , aby w pełni zaimplementować kolory o wysokim kontraście.

#### <a name="to-change-the-color-of-items-in-the-editor"></a>Aby zmienić kolor elementów w edytorze

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

2. W folderze **środowisko** wybierz pozycję **czcionki i kolory**.

3. W obszarze **Pokaż ustawienia dla**wybierz **Edytor tekstu**.

4. Z **elementów wyświetlanych**wybierz element, którego ekran należy zmienić, na przykład **zwykły tekst**, **margines wskaźnika**, **widoczny odstęp**, **nazwa atrybutu HTML**lub **atrybut XML**.

5. Wybierz pozycję Ustawienia wyświetlania z następujących opcji: **Pierwszy plan elementu**, **tło elementu**ipogrubienie.

6. Wybierz **OK**.

## <a name="toolbars"></a>Paski narzędzi

Aby poprawić użyteczność i dostępność paska narzędzi, możesz dodać tekst do przycisków paska narzędzi.

### <a name="to-assign-text-to-toolbar-buttons"></a>Aby przypisać tekst do przycisków paska narzędzi

1. W menu **Narzędzia** wybierz polecenie **Dostosuj**.

2. W oknie dialogowym **Dostosowywanie** wybierz kartę **polecenia** .

3. Wybierz pozycję **pasek narzędzi** , a następnie wybierz nazwę paska narzędzi zawierającego przycisk, dla którego ma być wyświetlany tekst.

4. Z listy wybierz polecenie, które ma zostać zmienione.

5. Wybierz **Modyfikuj zaznaczenie**.

6. Wybierz **obraz i tekst**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Aby zmodyfikować wyświetlany tekst na przycisku

1. Wybierz pozycję **Modyfikuj zaznaczenie**.

2. Obok **nazwy**w polu Wstaw Podaj nowy podpis dla wybranego przycisku.

## <a name="see-also"></a>Zobacz także

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Zasoby do projektowania dostępnych aplikacji](../../ide/reference/resources-for-designing-accessible-applications.md)