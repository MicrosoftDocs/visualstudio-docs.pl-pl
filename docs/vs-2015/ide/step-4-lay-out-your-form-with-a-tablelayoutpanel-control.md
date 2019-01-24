---
title: Krok 4. Określić układ formularza z formantem TableLayoutPanel | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8807272ddac0be12fe8a6d80f0aa8e9425307d89
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763274"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4. Określanie układu formularza przy użyciu kontrolki TableLayoutPanel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym kroku dodasz `TableLayoutPanel` formantu do formularza. TableLayoutPanel pomaga poprawnie wyrównać formanty w formularzu, który zostanie dodany później.  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 2](http://go.microsoft.com/fwlink/?LinkId=205211) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# — wideo 2](http://go.microsoft.com/fwlink/?LinkId=205200). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Aby zmienić układ formularza z formantem TableLayoutPanel  
  
1.  Po lewej stronie programu Visual Studio IDE, Znajdź **przybornika** kartę. Wybierz **przybornika** kartę i Przybornik pojawi się. (Lub na pasku menu wybierz **widoku**, **przybornika**.)  
  
2.  Wybierz symbol małego trójkąta obok **kontenery** grupę, aby ją otworzyć, jak pokazano na poniższej ilustracji.  
  
     ![Grupa kontenerów](../ide/media/express-toolbox.png "Express_Toolbox")  
Grupa kontenerów  
  
3.  Możesz dodać formanty, takie jak przyciski, pola wyboru i etykiet do formularza. Kliknij dwukrotnie `TableLayoutPanel` kontrolki z przybornika. (Można także można przeciągnąć kontrolki z przybornika do formularza). Gdy to zrobisz, IDE dodaje `TableLayoutPanel` sterowania do formularza, jak pokazano na poniższej ilustracji.  
  
     ![Formant TableLayoutPanel](../ide/media/express-formtablelayout.png "Express_FormTableLayout")  
TableLayoutPanel — formant  
  
    > [!NOTE]
    >  Po dodaniu TableLayoutPanel, jeśli okno pojawia się wewnątrz formularza z tytułem **zadania formantu TableLayoutPanel**, wybierz dowolne miejsce wewnątrz formularza, aby je zamknąć. Więcej informacji na temat tego okna przedstawiono w dalszej części tego samouczka.  
  
     Zwróć uwagę, jak Przybornik rozszerza się do objęcia formularza po wybraniu jego karty i zamyka się po wybierz dowolne miejsce poza nią. To jest funkcja Autoukrywanie IDE. Można włączyć tej funkcji dla każdego okna wybierając ikonę pinezki w prawym górnym rogu okna, aby przełączać automatyczne ukrywanie i blokowanie w miejscu. Ikona Pinezka wygląda następująco.  
  
     ![Ikona pinezki](../ide/media/express-pushpintoolbox.png "Express_PushpinToolbox")  
Ikona pinezki  
  
4.  Upewnij się, **TableLayoutPanel** jest zaznaczone, wybierając ją. Możesz sprawdzić, jaki formant jest zaznaczony, patrząc na liście rozwijanej w górnej części **właściwości** okna, jak pokazano na poniższej ilustracji.  
  
     ![Okno właściwości pokazujące formant TableLayoutPanel](../ide/media/express-controlspropwin.png "Express_ControlsPropWin")  
Okno właściwości pokazujące formant TableLayoutPanel  
  
5.  Wybierz **alfabetycznie** przycisk na pasku narzędzi w **właściwości** okna. Powoduje to, że lista właściwości w **właściwości** okno, aby wyświetlić w kolejności alfabetycznej, co ułatwi lokalizowanie właściwości w tym samouczku.  
  
6.  Selektor formantu to listy rozwijanej w górnej części **właściwości** okna. W tym przykładzie jej pokazują, że formant nazywany `tableLayoutPanel1` jest zaznaczone. Można wybierać formanty wybierając obszar w programie Windows Forms Designer lub wybierając z selektora formantów. Teraz, gdy `TableLayoutPanel` jest zaznaczone, Znajdź **Dock** właściwości i wybierz polecenie **Dock**, powinien być ustawiony na **Brak**. Należy zauważyć, że strzałki listy rozwijanej pojawia się obok wartości. Wybierz strzałkę, a następnie wybierz **wypełnienia** przycisku (duży przycisk na środku), jak pokazano na poniższej ilustracji.  
  
     ![Okno właściwości z zaznaczonym wypełnieniem](../ide/media/express-docktable.png "Express_DockTable")  
Okno właściwości z zaznaczonym wypełnieniem  
  
     *Dokowanie* w programie Visual Studio odnosi się do gdy okno jest dołączone do innego okna lub obszaru w IDE. Na przykład okno właściwości może być oddokowane — czyli niezamocowane programu Visual Studio — i lub może być zadokowane przy **Eksploratora rozwiązań**.  
  
7.  Po ustawieniu TableLayoutPanel **Dock** właściwości **wypełnienia**, panel wypełnia cały formularz. Jeśli zmienisz rozmiar formularza ponownie, obiekt TableLayoutPanel pozostaje zadokowany i zmienia się, aby dopasować rozmiar.  
  
    > [!NOTE]
    >  Element TableLayoutPanel działa jak tabela w programie Microsoft Office Word: Ma ona wierszy i kolumn i pojedyncze komórki może obejmować wiele wierszy i kolumn. Każda komórka może zawierać jeden formant (jak przycisk, pole wyboru lub etykietę). Twój TableLayoutPanel będzie miał `PictureBox` obejmujące cały górny wiersz, formant `CheckBox` kontrolki w jego lewej dolnej komórce i cztery `Button` kontrolki w jej dolnej prawej komórce.  
  
8.  Obecnie TableLayoutPanel ma dwa równe rzędy wielkości i dwie kolumny równej wielkości. Musisz zmienić ich rozmiar, aby górny wiersz i prawa kolumna były znacznie większe. W programie Windows Forms Designer wybierz obiekt TableLayoutPanel. W prawym górnym rogu jest przycisk mały trójkąt czarny, który wygląda następująco.  
  
     ![Przycisk z trójkątem](../ide/media/express-iconblacktriangle.gif "Express_IconBlackTriangle")  
Trójkątny przycisk  
  
     Ten przycisk oznacza, że kontrolka ma zadań, które ułatwiają automatycznym ustawianiu jego właściwości.  
  
9. Wybierz trójkąt, aby wyświetlić listę zadań kontroli, jak pokazano na poniższej ilustracji.  
  
     ![Zadania TableLayoutPanel](../ide/media/express-tablepanel.png "Express_TablePanel")  
Zadania TableLayoutPanel  
  
10. Wybierz **Edytuj wiersze i kolumny** zadanie, aby wyświetlić **Style kolumn i wierszy** okna. Wybierz **Kolumna1**i ustaw jej rozmiar na 15 procent, upewniając się, że **procent** przycisku jest zaznaczony i wprowadzono `15` w **procent** pole. (To `NumericUpDown` formantu, którego będziesz używać później w samouczku.) Wybierz **Kolumna2** i ustaw ją na 85 procent. Nie należy wybierać **OK** przycisk, ponieważ okno zostanie zamknięte. (Ale jeśli to zrobisz, możesz uruchomić go za pomocą listy zadań).  
  
     ![Style wierszy i kolumn TableLayoutPanel](../ide/media/vs-tablelayoutpanel-setup.png "VS_TableLayoutPanel_Setup")  
Style wierszy i kolumn TableLayoutPanel  
  
11. Z **Pokaż** listy rozwijanej w górnej części okna wybierz **wierszy**. Ustaw **Row1** do 90 procent a **Row2** do 10 procent.  
  
12. Wybierz **OK** przycisku. Twój TableLayoutPanel teraz powinien mieć duży, górny wiersz, mały dolny wiersz, małą lewą kolumnę i dużą prawą kolumnę. Możesz zmienić rozmiar wierszy i kolumn w TableLayoutPanel wybierając tableLayoutPanel1 w formularzu, a następnie przeciągając jego obramowania wierszy i kolumn.  
  
     ![Formularz Form1 z o zmienionym rozmiarze TableLayoutPanel](../ide/media/vs-formafterlayoutpanel.png "VS_FormAfterLayoutPanel")  
Formularz Form1 z po zmianie rozmiaru formantu TableLayoutPanel  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodawanie formantów do formularza](../ide/step-5-add-controls-to-your-form.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md).
