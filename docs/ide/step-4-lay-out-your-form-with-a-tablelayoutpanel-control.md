---
title: Krok 4. Określić układ formularza z formantem TableLayoutPanel
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94e0c5999f8d8e6bdfbc96a24a1a51b7c093aca1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431461"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4. Określić układ formularza z formantem TableLayoutPanel
W tym kroku dodasz <xref:System.Windows.Forms.TableLayoutPanel> formantu do formularza. TableLayoutPanel pomaga poprawnie wyrównać formanty w formularzu, który zostanie dodany później.

 ![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 2](http://go.microsoft.com/fwlink/?LinkId=205211) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# -2 wideo](http://go.microsoft.com/fwlink/?LinkId=205200). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Aby zmienić układ formularza z formantem TableLayoutPanel

1. Po lewej stronie programu Visual Studio IDE, Znajdź **przybornika** kartę. Wybierz **przybornika** kartę, a **przybornika** pojawia się. (Lub na pasku menu wybierz **widoku** > **przybornika**.)

2. Wybierz symbol małego trójkąta obok **kontenery** grupę, aby ją otworzyć, jak pokazano na poniższej ilustracji.

     ![Grupa kontenerów](../ide/media/express_toolbox.png)
**kontenery** grupy

3. Możesz dodać formanty, takie jak przyciski, pola wyboru i etykiet do formularza. Kliknij dwukrotnie formant TableLayoutPanel w **przybornika**. (Można także można przeciągnąć kontrolki z przybornika do formularza). Gdy to zrobisz, IDE dodaje formant TableLayoutPanel do formularza, jak pokazano na poniższej ilustracji.

     ![Formant TableLayoutPanel](../ide/media/express_formtablelayout.png)
**TableLayoutPanel** kontroli

    > [!NOTE]
    > Po dodaniu TableLayoutPanel, jeśli okno pojawia się wewnątrz formularza z tytułem **zadania formantu TableLayoutPanel**, wybierz dowolne miejsce wewnątrz formularza, aby je zamknąć. Więcej informacji na temat tego okna przedstawiono w dalszej części tego samouczka.

     Zwróć uwagę sposób, w jaki **przybornika** rozwija do objęcia formularza po wybraniu jego karty i zamyka się po wybierz dowolne miejsce poza nią. To jest funkcja Autoukrywanie IDE. Można włączyć tej funkcji dla każdego okna wybierając ikonę pinezki w prawym górnym rogu okna, aby przełączać automatyczne ukrywanie i blokowanie w miejscu. Ikona Pinezka wygląda następująco.

     ![Ikona pinezki](../ide/media/express_pushpintoolbox.png)
**pinezki** ikony

4. Upewnij się, że TableLayoutPanel jest zaznaczony, wybierając je. Możesz sprawdzić, jaki formant jest zaznaczony, patrząc na liście rozwijanej w górnej części **właściwości** okna, jak pokazano na poniższej ilustracji.

     ![Okno właściwości pokazujące formant TableLayoutPanel](../ide/media/express_controlspropwin.png)
**właściwości** okno **TableLayoutPanel** kontroli

5. Wybierz **alfabetycznie** przycisk na pasku narzędzi w **właściwości** okna. Powoduje to, że lista właściwości w **właściwości** okno, aby wyświetlić w kolejności alfabetycznej, co ułatwi lokalizowanie właściwości w tym samouczku.

6. Selektor formantu to listy rozwijanej w górnej części **właściwości** okna. W tym przykładzie jej pokazują, że formant nazywany `tableLayoutPanel1` jest zaznaczone. Możesz wybierać formanty, albo przez wybranie obszaru w **Windows Forms Designer** lub wybierając z selektora formantów. Teraz, że TableLayoutPanel jest zaznaczony, znaleźć **Dock** właściwości i wybierz polecenie **Dock**, powinien być ustawiony na **Brak**. Należy zauważyć, że strzałki listy rozwijanej pojawia się obok wartości. Wybierz strzałkę, a następnie wybierz **wypełnienia** przycisku (duży przycisk na środku), jak pokazano na poniższej ilustracji.

     ![Okno właściwości z zaznaczonym wypełnieniem](../ide/media/express_docktable.png)
**właściwości** okno z **wypełnienia** wybrane

     *Dokowanie* w programie Visual Studio odnosi się do gdy okno jest dołączone do innego okna lub obszaru w IDE. Na przykład **właściwości** okno może być oddokowane — czyli niezamocowane Visual Studio — i lub może być zadokowane przy **Eksploratora rozwiązań**.

7. Po ustawieniu TableLayoutPanel **Dock** właściwości **wypełnienia**, panel wypełnia cały formularz. Jeśli zmienisz rozmiar formularza ponownie, obiekt TableLayoutPanel pozostaje zadokowany i zmienia się, aby dopasować rozmiar.

    > [!NOTE]
    > Element TableLayoutPanel działa jak tabela w programie Microsoft Office Word: Ma ona wierszy i kolumn i pojedyncze komórki może obejmować wiele wierszy i kolumn. Każda komórka może zawierać jeden formant (jak przycisk, pole wyboru lub etykietę). Twój TableLayoutPanel będzie miał <xref:System.Windows.Forms.PictureBox> obejmujące cały górny wiersz, formant <xref:System.Windows.Forms.CheckBox> kontrolki w jego lewej dolnej komórce i cztery <xref:System.Windows.Forms.Button> kontrolki w jej dolnej prawej komórce.

8. Obecnie TableLayoutPanel ma dwa równe rzędy wielkości i dwie kolumny równej wielkości. Musisz zmienić ich rozmiar, aby górny wiersz i prawa kolumna były znacznie większe. W **Windows Forms Designer**, wybierz obiekt TableLayoutPanel. W prawym górnym rogu jest przycisk mały trójkąt czarny, który wygląda następująco.

     ![Przycisk z trójkątem](../ide/media/express_iconblacktriangle.gif)
**trójkąt** przycisku

     Ten przycisk oznacza, że kontrolka ma zadań, które ułatwiają automatycznym ustawianiu jego właściwości.

9. Wybierz trójkąt, aby wyświetlić listę zadań kontroli, jak pokazano na poniższej ilustracji.

     ![Zadania TableLayoutPanel](../ide/media/express_tablepanel.png)
**TableLayoutPanel** zadania

10. Wybierz **Edytuj wiersze i kolumny** zadanie, aby wyświetlić **Style kolumn i wierszy** okna. Wybierz **Kolumna1**i ustaw jej rozmiar na 15 procent, upewniając się, że **procent** przycisku jest zaznaczony i wprowadzono **15** w **procent** pole. (To <xref:System.Windows.Forms.NumericUpDown> formantu, którego będziesz używać później w samouczku.) Wybierz **Kolumna2** i ustaw ją na 85 procent. Nie należy wybierać **OK** przycisk, ponieważ okno zostanie zamknięte. (Ale jeśli to zrobisz, możesz uruchomić go za pomocą listy zadań).

     ![Style wierszy i kolumn TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)
**TableLayoutPanel** style wierszy i kolumn

11. Z **Pokaż** listy rozwijanej w górnej części okna wybierz **wierszy**. Ustaw **Row1** do 90 procent a **Row2** do 10 procent.

12. Wybierz **OK** przycisku. Twój TableLayoutPanel teraz powinien mieć duży, górny wiersz, mały dolny wiersz, małą lewą kolumnę i dużą prawą kolumnę. Możesz zmienić rozmiar wierszy i kolumn w TableLayoutPanel wybierając **tableLayoutPanel1** w formularzu, a następnie przeciągając jego obramowania wierszy i kolumn.

     ![Formularz Form1 z o zmienionym rozmiarze TableLayoutPanel](../ide/media/vs_formafterlayoutpanel.png)
**Form1** przy zmianie rozmiaru **TableLayoutPanel**

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodawanie formantów do formularza](../ide/step-5-add-controls-to-your-form.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md).
