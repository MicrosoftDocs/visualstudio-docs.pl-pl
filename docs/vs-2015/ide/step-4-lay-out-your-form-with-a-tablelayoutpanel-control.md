---
title: Krok 4. układ formularza przy użyciu formantu TableLayoutPanel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f61a308fcd68b03852176087438c22c245078693
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851544"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4. Określenie układu formularza przy użyciu formantu TableLayoutPanel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym kroku dodasz kontrolkę `TableLayoutPanel` do formularza. TableLayoutPanel pomaga prawidłowo wyrównać kontrolki w formularzu, który zostanie później dodany.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 2](https://msdn.microsoft.com/vbasic/gg315945.aspx) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# pliku wideo 2](https://msdn.microsoft.com/vcsharp/gg278410.aspx). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Aby określić układ formularza przy użyciu kontrolki TableLayoutPanel

1. Po lewej stronie środowiska IDE programu Visual Studio Znajdź kartę **Przybornik** . Wybierz kartę **Przybornik** i pojawi się Przybornik. (Lub na pasku menu wybierz **Widok**, **Przybornik**).

2. Wybierz mały trójkątny symbol obok grupy **kontenery** , aby go otworzyć, jak pokazano na poniższej ilustracji.

     ![Grupa kontenerów](../ide/media/express-toolbox.png "Express_Toolbox") Grupa kontenerów

3. Kontrolki, takie jak przyciski, pola wyboru i etykiety, można dodawać do formularza. Kliknij dwukrotnie formant `TableLayoutPanel` w przyborniku. (Możesz też przeciągnąć kontrolkę z przybornika na formularz). Gdy to zrobisz, IDE doda do formularza formant `TableLayoutPanel`, jak pokazano na poniższej ilustracji.

     ![TableLayoutPanel — formant](../ide/media/express-formtablelayout.png "Express_FormTableLayout") TableLayoutPanel — formant

    > [!NOTE]
    > Po dodaniu TableLayoutPanel, jeśli okno jest wyświetlane w formularzu z tytułem **zadania TableLayoutPanel**, Wybierz dowolne miejsce wewnątrz formularza, aby je zamknąć. Więcej informacji na temat tego okna znajdziesz w dalszej części tego samouczka.

     Zauważ, jak Przybornik rozszerza się, aby pokryć formularz po wybraniu jego karty, i jest zamykany po wybraniu dowolnego miejsca poza nim. Jest to funkcja autoukrywania środowiska IDE. Można ją włączyć lub wyłączyć dla dowolnego systemu Windows, wybierając ikonę pinezki w prawym górnym rogu okna, aby przełączyć funkcję Autoukrywanie i zablokować ją w miejscu. Ikona pinezki jest wyświetlana w następujący sposób.

     ![Ikona pinezki](../ide/media/express-pushpintoolbox.png "Express_PushpinToolbox") Ikona pinezki

4. Upewnij się, że wybrano element **TableLayoutPanel** , wybierając go. Można sprawdzić, jaki formant jest zaznaczony, przeglądając listę rozwijaną w górnej części okna **Właściwości** , jak pokazano na poniższej ilustracji.

     ![Okno właściwości pokazujący formant TableLayoutPanel](../ide/media/express-controlspropwin.png "Express_ControlsPropWin") okno Właściwości pokazujący formant TableLayoutPanel

5. Wybierz przycisk **alfabetyczny** na pasku narzędzi w oknie **Właściwości** . Powoduje to, że lista właściwości w oknie **Właściwości** będzie wyświetlana w kolejności alfabetycznej, co ułatwia lokalizowanie właściwości w tym samouczku.

6. Selektor kontrolki jest listą rozwijaną u góry okna **Właściwości** . W tym przykładzie pokazuje, że wybrano kontrolkę o nazwie `tableLayoutPanel1`. Możesz wybrać kontrolki, wybierając obszar w Projektant formularzy systemu Windows lub wybierając z selektora kontrolki. Teraz, gdy `TableLayoutPanel` jest zaznaczone, Znajdź właściwość **Dock** i wybierz opcję **Dock**, która powinna mieć wartość **none**. Zauważ, że obok wartości zostanie wyświetlona strzałka listy rozwijanej. Wybierz strzałkę, a następnie wybierz przycisk **wypełnienie** (duży przycisk w środku), jak pokazano na poniższej ilustracji.

     ![Okno właściwości z wybranym wypełnieniem](../ide/media/express-docktable.png "Express_DockTable") okno Właściwości z wybranym wypełnieniem

     *Dokowanie* w programie Visual Studio odnosi się do sytuacji, gdy okno jest dołączone do innego okna lub obszaru w IDE. Na przykład okno Właściwości mogą być oddokowane, czyli niedołączone i swobodne w programie Visual Studio — lub mogą być zadokowane względem **Eksplorator rozwiązań**.

7. Po ustawieniu właściwości **Dock dokowania** na **wypełnienie**panel wypełnia cały formularz. Jeśli zmienisz rozmiar formularza ponownie, TableLayoutPanel zostanie zadokowane i dopasowuje się do dopasowania.

    > [!NOTE]
    > TableLayoutPanel działa jak tabela w Microsoft Office Word: zawiera wiersze i kolumny, a pojedyncza komórka może obejmować wiele wierszy i kolumn. Każda komórka może zawierać jedną kontrolkę (na przykład przycisk, pole wyboru lub etykietę). Obiekt TableLayoutPanel będzie miał `PictureBox`ą kontrolkę obejmującą cały górny wiersz, `CheckBox` kontrolkę w lewej dolnej komórce i cztery `Button` kontrolki w swojej prawej dolnej komórce.

8. Obecnie TableLayoutPanel ma dwa wiersze o równym rozmiarze i dwie kolumny o równym rozmiarze. Należy zmienić ich rozmiar, aby górny wiersz i prawa kolumna były znacznie większe. W Projektant formularzy systemu Windows wybierz TableLayoutPanel. W prawym górnym rogu znajduje się mały czarny trójkątny przycisk, który pojawia się w następujący sposób.

     ![Przycisk trójkąta](../ide/media/express-iconblacktriangle.gif "Express_IconBlackTriangle") Przycisk trójkąta

     Ten przycisk oznacza, że Kontrolka zawiera zadania, które ułatwiają automatyczne ustawianie jego właściwości.

9. Wybierz Trójkąt, aby wyświetlić listę zadań kontrolki, jak pokazano na poniższej ilustracji.

     ![Zadania TableLayoutPanel](../ide/media/express-tablepanel.png "Express_TablePanel") Zadania TableLayoutPanel

10. Wybierz zadanie **Edytuj wiersze i kolumny** , aby wyświetlić okno **Style kolumn i wierszy** . Wybierz pozycję **Kolumna1**i ustaw jej rozmiar na 15 procent, upewniając się, że jest zaznaczony przycisk **procent** i wprowadzając `15` w polu **procent** . (To jest formant `NumericUpDown`, którego będziesz używać w kolejnym samouczku). Wybierz pozycję **Kolumna2** i ustaw ją na 85 procent. Nie wybieraj jeszcze przycisku **OK** , ponieważ okno zostanie zamknięte. (Ale jeśli to zrobisz, możesz otworzyć go ponownie za pomocą listy zadań).

     ![Kolumny TableLayoutPanel i style wierszy](../ide/media/vs-tablelayoutpanel-setup.png "VS_TableLayoutPanel_Setup") Kolumny TableLayoutPanel i style wierszy

11. Z listy rozwijanej **Pokaż** w górnej części okna wybierz pozycję **wiersze**. Ustaw wartość **row1** na 90% i **Row2** na 10 procent.

12. Wybierz **OK** przycisku. Obiekt TableLayoutPanel powinien teraz mieć duży górny wiersz, mały dolny wiersz, małą lewą kolumnę i dużą prawą kolumnę. Można zmienić rozmiar wierszy i kolumn w TableLayoutPanel, wybierając tableLayoutPanel1 w formularzu, a następnie przeciągając obramowania wierszy i kolumn.

     ![Formularz Form1 ze zmienionym rozmiarem TableLayoutPanel](../ide/media/vs-formafterlayoutpanel.png "VS_FormAfterLayoutPanel") Formularz Form1 ze zmienionym rozmiarem TableLayoutPanel

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md).
