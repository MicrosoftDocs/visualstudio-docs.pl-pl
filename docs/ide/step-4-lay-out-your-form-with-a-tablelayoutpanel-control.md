---
title: Krok 4. Określanie układu formularza przy użyciu kontrolki TableLayoutPanel
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 269fa26b89ab1ca9165efa8eb8971731f078ec60
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925936"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4. Określanie układu formularza przy użyciu kontrolki TableLayoutPanel
W tym kroku dodasz <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę do formularza. TableLayoutPanel pomaga prawidłowo wyrównać kontrolki w formularzu, który zostanie później dodany.

![link do wideo](../data-tools/media/playvideo.gif)dla wersji wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 2](http://go.microsoft.com/fwlink/?LinkId=205211) lub [samouczek 1: Utwórz przeglądarkę obrazów w C# pliku-wideo 2](http://go.microsoft.com/fwlink/?LinkId=205200). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Aby określić układ formularza przy użyciu kontrolki TableLayoutPanel

1. Po lewej stronie środowiska IDE programu Visual Studio Znajdź kartę **Przybornik** . Wybierz kartę **Przybornik** i pojawi się **Przybornik** . (Lub na pasku menu wybierz**Przybornik** **widoku** > ).

2. Wybierz mały trójkątny symbol obok grupy **kontenery** , aby go otworzyć, jak pokazano na poniższej ilustracji.

     ![Grupa](../ide/media/express_toolbox.png)
**kontenerów** grupy kontenerów

3. Kontrolki, takie jak przyciski, pola wyboru i etykiety, można dodawać do formularza. Kliknij dwukrotnie formant TableLayoutPanel w przyborniku. (Możesz też przeciągnąć kontrolkę z przybornika na formularz). Gdy to zrobisz, IDE dodaje formant TableLayoutPanel do formularza, jak pokazano na poniższej ilustracji.

     ![TableLayoutPanel — formant TableLayoutPanel kontrolki ](../ide/media/express_formtablelayout.png)


    > [!NOTE]
    > Po dodaniu TableLayoutPanel, jeśli okno jest wyświetlane w formularzu z tytułem **zadania TableLayoutPanel**, Wybierz dowolne miejsce wewnątrz formularza, aby je zamknąć. Więcej informacji na temat tego okna znajdziesz w dalszej części tego samouczka.

     Zauważ, jak **Przybornik** rozszerza się, aby pokryć formularz po wybraniu jego karty, i jest zamykany po wybraniu dowolnego miejsca poza nim. Jest to funkcja autoukrywania środowiska IDE. Można ją włączyć lub wyłączyć dla dowolnego systemu Windows, wybierając ikonę pinezki w prawym górnym rogu okna, aby przełączyć funkcję Autoukrywanie i zablokować ją w miejscu. Ikona pinezki jest wyświetlana w następujący sposób.

     ![Ikona pinezki w ikonie](../ide/media/express_pushpintoolbox.png)
pinezki

4. Upewnij się, że TableLayoutPanel jest zaznaczone, wybierając ją. Można sprawdzić, jaki formant jest zaznaczony, przeglądając listę rozwijaną w górnej części okna **Właściwości** , jak pokazano na poniższej ilustracji.

     ![Okno właściwości wyświetlanie okna](../ide/media/express_controlspropwin.png)
**Właściwości** formantu TableLayoutPanel z kontrolką **TableLayoutPanel**

5. Wybierz przycisk **alfabetyczny** na pasku narzędzi w oknie **Właściwości** . Powoduje to, że lista właściwości w oknie **Właściwości** będzie wyświetlana w kolejności alfabetycznej, co ułatwia lokalizowanie właściwości w tym samouczku.

6. Selektor kontrolki jest listą rozwijaną u góry okna **Właściwości** . W tym przykładzie pokazuje, że wybrano kontrolkę `tableLayoutPanel1` o nazwie. Możesz wybrać kontrolki, wybierając obszar w **Projektant formularzy systemu Windows** lub wybierając z selektora kontrolki. Teraz, gdy wybrano TableLayoutPanel, Znajdź właściwość **Dock** i wybierz opcję **Dock**, która powinna mieć wartość **none**. Zauważ, że obok wartości zostanie wyświetlona strzałka listy rozwijanej. Wybierz strzałkę, a następnie wybierz przycisk **wypełnienie** (duży przycisk w środku), jak pokazano na poniższej ilustracji.

     ![Okno właściwości z oknem Wypełnij](../ide/media/express_docktable.png)
wybrane**Właściwości** z wybranym wypełnieniem

     *Dokowanie* w programie Visual Studio odnosi się do sytuacji, gdy okno jest dołączone do innego okna lub obszaru w IDE. Na przykład okno **Właściwości** może być oddokowane, czyli niedołączone i swobodne w programie Visual Studio — lub może być zadokowane względem **Eksplorator rozwiązań**.

7. Po ustawieniu właściwości **Dock dokowania** na **wypełnienie**panel wypełnia cały formularz. Jeśli zmienisz rozmiar formularza ponownie, TableLayoutPanel zostanie zadokowane i dopasowuje się do dopasowania.

    > [!NOTE]
    > TableLayoutPanel działa jak tabela w Microsoft Office Word: Zawiera wiersze i kolumny, a pojedyncza komórka może obejmować wiele wierszy i kolumn. Każda komórka może zawierać jedną kontrolkę (na przykład przycisk, pole wyboru lub etykietę). Obiekt <xref:System.Windows.Forms.PictureBox> TableLayoutPanel będzie miał kontrolkę obejmującą cały górny wiersz <xref:System.Windows.Forms.CheckBox> , kontrolkę w lewej dolnej komórce i cztery <xref:System.Windows.Forms.Button> kontrolki w swojej prawej dolnej komórce.

8. Obecnie TableLayoutPanel ma dwa wiersze o równym rozmiarze i dwie kolumny o równym rozmiarze. Należy zmienić ich rozmiar, aby górny wiersz i prawa kolumna były znacznie większe. W **Projektant formularzy systemu Windows**wybierz TableLayoutPanel. W prawym górnym rogu znajduje się mały czarny trójkątny przycisk, który pojawia się w następujący sposób.

     ![Trójkątny](../ide/media/express_iconblacktriangle.gif)
przycisk**trójkąta** przycisku

     Ten przycisk oznacza, że Kontrolka zawiera zadania, które ułatwiają automatyczne ustawianie jego właściwości.

9. Wybierz Trójkąt, aby wyświetlić listę zadań kontrolki, jak pokazano na poniższej ilustracji.

     ![TableLayoutPanel zadań](../ide/media/express_tablepanel.png)
TableLayoutPanel — zadania

10. Wybierz zadanie **Edytuj wiersze i kolumny** , aby wyświetlić okno **Style kolumn i wierszy** . Wybierz pozycję **Kolumna1**, a następnie ustaw jej rozmiar na 15 procent, upewniając się, że jest zaznaczony przycisk **procent** i wprowadzając wartość **15** w polu **procent** . (To jest <xref:System.Windows.Forms.NumericUpDown> kontrolka, która będzie używana w kolejnym samouczku). Wybierz pozycję **Kolumna2** i ustaw ją na 85 procent. Nie wybieraj jeszcze przycisku **OK** , ponieważ okno zostanie zamknięte. (Ale jeśli to zrobisz, możesz otworzyć go ponownie za pomocą listy zadań).

     ![Kolumny TableLayoutPanel i style](../ide/media/vs_tablelayoutpanel_setup.png)
wierszy kolumny**TableLayoutPanel** i style wierszy

11. Z listy rozwijanej **Pokaż** w górnej części okna wybierz pozycję **wiersze**. Ustaw wartość **row1** na 90% i **Row2** na 10 procent.

12. Wybierz **OK** przycisku. Obiekt TableLayoutPanel powinien teraz mieć duży górny wiersz, mały dolny wiersz, małą lewą kolumnę i dużą prawą kolumnę. Można zmienić rozmiar wierszy i kolumn w TableLayoutPanel, wybierając **tableLayoutPanel1** w formularzu, a następnie przeciągając obramowania wierszy i kolumn.

     ![Formularz Form1 ze zmienionym rozmiarem TableLayoutPanel](../ide/media/vs_formafterlayoutpanel.png)
**Form1** ze zmienionym rozmiarem **TableLayoutPanel**

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodaj formanty do formularza](../ide/step-5-add-controls-to-your-form.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3. Ustaw właściwości](../ide/step-3-set-your-form-properties.md)formularza.
