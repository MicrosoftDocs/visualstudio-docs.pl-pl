---
title: 'Instrukcje: Ustawianie opcji ułatwień dostępu środowiska IDE'
description: Dowiedz się, jak ustawić opcje ułatwień dostępu w programie Visual Studio, który ułatwi jego zintegrowanego środowiska programistycznego (IDE) dla każdego, w tym dla osób niedowidzących do odczytu, jak i dla osób o ograniczonej sprawności ruchowej, aby zapisać.
ms.date: 08/22/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c8fa92644221149d3405eea25b1c85e229861e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906777"
---
# <a name="how-to-set-ide-accessibility-options"></a>Instrukcje: Ustawianie opcji ułatwień dostępu środowiska IDE

> [!TIP]
> Aby dowiedzieć się więcej o najnowszych aktualizacjach ułatwień dostępu, zobacz [ulepszenia ułatwień dostępu w programie Visual Studio 2017 w wersji 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) wpis w blogu.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawiera funkcje, które ułatwiają dla osób niedowidzących do odczytu, a także dla osób o ograniczonej sprawności ruchowej, aby zapisać. Funkcje te obejmują, zmienianie rozmiaru i koloru tekstu w edytorach, zmieniając rozmiar tekstu i przycisków na paskach narzędzi i automatycznego uzupełniania dla metod i parametrów, kilka.

Ponadto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje układy klawiatury Dvoraka, które powodują, że najczęściej wpisane znaki łatwiej dostępne. Można również dostosować domyślne klawiszy skrótu dostępnych z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../environment-settings.md#reset-settings).

## <a name="editors-dialogs-and-tool-windows"></a>Edytory, okna dialogowe i okna narzędzi

 Domyślnie, okna dialogowe i okna narzędzi w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używać tego samego rozmiaru czcionki i kolory jako systemu operacyjnego. Ustawienia kolorów dla ramki w IDE, okna dialogowe, paski narzędzi i okien narzędzi opierają się schemat kolorów: jasny i ciemny. Możesz zmienić bieżący motyw kolorów w [ogólne, środowisko, opcje, okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md).

 Można także wyświetlić wyskakującego okienka, w widoku kodu w edytorze. Te okna można monitują dostępni członkowie na bieżący obiekt i parametry do wykonania funkcji lub instrukcji. Okna te mogą być przydatne, jeśli masz problemy z pisaniem. Jednak przeszkadzają fokus w edytorze kodu, który może być problematyczne dla niektórych użytkowników. Można wyłączyć te okna, otwierając okno dialogowe Opcje i wyczyszczenie **automatyczna lista członków** i **informacje o parametrach** w **edytora tekstów**, **wszystkie Języki**, **ogólne** strony w **opcje** okno dialogowe.

 Możesz zmienić kolejność systemu windows w zintegrowanym środowisku programistycznym (IDE) stosownie do potrzeb sposobu pracy. Można zadokować, float, ukryć lub automatycznie ukrywaj każdego okna narzędzi.

 Aby uzyskać więcej informacji dotyczących sposobu zmieniania układy okna, zobacz [dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Zmiana rozmiaru tekstu

 Można zmienić ustawienia dla okien narzędzi oparte na tekście, takie jak **polecenia** oknie **bezpośrednie** oknie i **dane wyjściowe** okna w **czcionek i Kolory** okienku **środowiska** opcji na liście **narzędzia** okno dialogowe. Gdy **[wszystkie tekstowe narzędzie Windows]** wybrano w **Pokaż ustawienia dla** listy rozwijanej ustawieniem domyślnym jest wymieniony jako **domyślne** w **pierwszy plan elementu**  i **tła elementu** list rozwijanych. Ustawienia można również zmienić sposób wyświetlania tekstu w edytorze.

#### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Aby zmienić rozmiar tekstu w oknach narzędzi tekstowych i edytory

1.  Z **narzędzia** menu, wybierz **opcje**.

2.  Wybierz **czcionki i kolory** na **środowiska** folderu.

3.  Wybierz jedną z opcji na **Pokaż ustawienia dla** menu rozwijanego.

     Aby zmienić rozmiar czcionki dla tekstu w edytorze, wybierz **edytora tekstów**.

     Aby zmienić rozmiar czcionki dla tekstu w oknach narzędzi tekstowych, wybierz **[Windows wszystkie narzędzia Tekst]**.

     Aby zmienić rozmiar czcionki dla tekstu etykietki narzędzia w edytorze, wybierz **etykietki narzędzi edytora**.

     Aby zmienić rozmiar czcionki dla tekstu w wyskakujące okienka uzupełniania instrukcji, wybierz **uzupełniania instrukcji**.

4.  Z **wyświetlania elementów**, wybierz opcję **zwykły tekst**.

5.  W **czcionki**, wybierz nowy typ czcionki.

6.  W **rozmiar**, wybierz nowy rozmiar czcionki.

    > [!NOTE]
    > Aby zresetować rozmiar okna narzędzi tekstowych i edytorów, wybierz **Użyj ustawień domyślnych**.

7.  Wybierz **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Zmienianie kolorów, które są używane w środowisku IDE

 Możesz również zmienić kolory domyślne tekstu, wskaźniki margines, biały i elementy kodu w edytorze.

> [!NOTE]
> Aby użyć dużego kontrastu kolorów dla wszystkich aplikacji systemu windows w systemie operacyjnym, naciśnij klawisz po lewej stronie <strong>ALT +</strong>po lewej stronie **SHIFT + PRINT SCREEN**. Jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest otworzyć, zamknij i otwórz ponownie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do pełnego wdrożenia dużego kontrastu kolorów.

#### <a name="to-change-the-color-of-items-in-the-editor"></a>Aby zmienić kolor elementów w edytorze

1.  Z **narzędzia** menu, wybierz **opcje**.

2.  W **środowiska** folderu, wybierz **czcionki i kolory**.

3.  W **Pokaż ustawienia dla**, wybierz **edytora tekstów**.

4.  Z **wyświetlania elementów**, wybierz element, którego ekran zachodzi potrzeba zmiany, takie jak **zwykły tekst**, **margines wskaźnika**, **pokazuj biały znak**, **Nazwa atrybutu HTML**, lub **atrybutu XML**.

5.  Wybierz ustawienia wyświetlania spośród następujących opcji: **Pierwszy plan elementu**, **tła elementu**, i **Bold**.

6.  Wybierz **OK**.

## <a name="toolbars"></a>Paski narzędzi

 Aby zwiększyć użyteczność paska narzędzi i dostępność, można dodać tekstu do przycisków paska narzędzi.

### <a name="to-assign-text-to-toolbar-buttons"></a>Aby przypisać tekstu do przycisków paska narzędzi

1.  Z **narzędzia** menu, wybierz **Dostosuj**.

2.  W **Dostosuj** okno dialogowe, wybierz opcję **polecenia** kartę.

3.  Wybierz **narzędzi** , a następnie wybierz nazwę paska narzędzi, zawierający przycisk, mają do wyświetlania tekstu.

4.  Na liście wybierz polecenie, które chcesz zmienić.

5.  Wybierz **Modyfikuj zaznaczenie**.

6.  Wybierz **tekstowych i obrazów**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Aby zmodyfikować wyświetlanego tekstu przycisku

1.  Wybierz ponownie **Modyfikuj zaznaczenie**.

2.  Sąsiadujące w **nazwa**, Wstaw Podaj nowy podpis dla przycisku.

## <a name="see-also"></a>Zobacz także

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Zasoby do projektowania dostępnych aplikacji](../../ide/reference/resources-for-designing-accessible-applications.md)