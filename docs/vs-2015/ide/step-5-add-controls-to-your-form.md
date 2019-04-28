---
title: Krok 5. Dodawanie formantów do formularza | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e05e8c313e6c2345964386c9c4f08c1bb6f16089
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442555"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5. Dodawanie kontrolek do formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym kroku dodaj formanty, takie jak `PictureBox` kontroli i `CheckBox` formantu do formularza. Następnie dodaj przyciski do formularza.  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 2](http://go.microsoft.com/fwlink/?LinkId=205211) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# — wideo 2](http://go.microsoft.com/fwlink/?LinkId=205200). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-add-controls-to-your-form"></a>Aby dodać formanty do formularza  
  
1. Przejdź do karty Przybornik (znajduje się po lewej stronie programu Visual Studio IDE) i rozwiń **wspólnych formantów** grupy. To pokazuje najczęstsze formanty wyświetlane na formularzach.  
  
2. Wybierz formant TableLayoutPanel na formularzu. Aby sprawdzić, czy TableLayoutPanel jest zaznaczony, upewnij się, że jego nazwa jest wyświetlana w polu listy rozwijanej w górnej części **właściwości** okna. Można również wybrać formanty formularza za pomocą listy rozwijanej w górnej części **właściwości** okna. Wybieranie formantu w ten sposób może być często łatwiejsze niż Wybieranie formantu tiny za pomocą myszy.  
  
3. Kliknij dwukrotnie **PictureBox** element, aby dodać formant PictureBox do formularza. Ponieważ TableLayoutPanel jest zadokowany do wypełnienia formularza, IDE dodaje formant PictureBox do pierwszej pustej komórki (górny lewy róg).  
  
4. Wybierz nowy formant PictureBox, aby go zaznaczyć, a następnie wybierz czarny trójkąt na nowym formancie PictureBox w celu wyświetlenia jego listy zadań, jak pokazano na poniższej ilustracji.  
  
     ![Zadania w obiekcie PictureBox](../ide/media/express-pictureboxtasks.png "Express_PictureBoxTasks")  
Zadania w obiekcie PictureBox  
  
    > [!NOTE]
    > Jeśli przypadkowo dodasz nieprawidłowy typ formantu do swojego obiektu TableLayoutPanel, można go usunąć. Kliknij prawym przyciskiem myszy formant, a następnie wybierz **Usuń** jego menu kontekstowego. Można również usunąć formanty z formularza, korzystając z paska menu. Na pasku menu wybierz **Edytuj**, **Cofnij**, lub **Edytuj**, **Usuń**.  
  
5. Wybierz **Zadokuj w kontenerze nadrzędnym** łącza. To automatycznie ustawia element PictureBox **Dock** właściwości **wypełnienia**. Aby to zobaczyć, wybierz formant PictureBox, aby go zaznaczyć, przejdź do **właściwości** okna, i upewnij się, że **Dock** właściwość jest ustawiona na **wypełnienia**.  
  
6. Wprowadź obiekt PictureBox obejmuje obie kolumny, zmieniając jego **ColumnSpan** właściwości. Wybierz formant PictureBox i ustaw jego **ColumnSpan** właściwości **2**. Ponadto gdy element PictureBox jest pusty, należy wyświetlić pustą ramkę. Ustaw jego **BorderStyle** właściwości **Fixed3D**.  
  
    > [!NOTE]
    > Jeśli nie widzisz **ColumnSpan** właściwość dla swojego obiektu PictureBox, a następnie ją jest prawdopodobne, że element PictureBox został dodany do formularza, a nie obiekt TableLayoutPanel. Aby rozwiązać ten problem, wybierz PictureBox, usuń go, wybierz TableLayoutPanel, a następnie dodaj nowy PictureBox.  
  
7. Wybierz TableLayoutPanel na formularzu, a następnie dodaj **wyboru** formantu do formularza. Kliknij dwukrotnie **wyboru** w przyborniku, aby dodać nowy formant pola wyboru do następnej wolnej komórki w tabeli. Ponieważ PictureBox zajmuje pierwsze dwie komórki w TableLayoutPanel, formant pola wyboru jest dodawany do lewej dolnej komórce. Wybierz **tekstu** właściwość i wpisz wyraz **Stretch**, jak pokazano na poniższej ilustracji.  
  
     ![Formant TextBox z właściwością Stretch](../ide/media/express-pictureviewercheckbox.png "Express_PictureViewerCheckbox")  
Formant TextBox z właściwością Stretch  
  
8. Wybierz TableLayoutPanel na formularzu, a następnie przejdź do **kontenery** grupy w przyborniku (skąd masz formant TableLayoutPanel), a następnie kliknij dwukrotnie ikonę **FlowLayoutPanel** element, aby dodać nowy formant do ostatniej komórki w elemencie PictureBox (prawy dolny róg). Następnie Zadokuj FlowLayoutPanel w TableLayoutPanel (przez wybranie **Zadokuj w kontenerze nadrzędnym** na liście zadań programu FlowLayoutPanel czarny trójkąt lub przez ustawienie FlowLayoutPanel **zadokować** Właściwość **wypełnienia**).  
  
    > [!NOTE]
    > FlowLayoutPanel jest kontenerem, który organizuje inne formanty w czyste rzędy w kolejności. Po zmianie rozmiaru FlowLayoutPanel, jeśli jest wystarczająca ilość miejsca, aby zmienić układ wszystkie formanty w jednym wierszu, robi to. W przeciwnym razie układa je w linie, jedną nad drugą. FlowLayoutPanel będzie służyć do przechowywania czterech przycisków. Jeśli przyciski są umieszczane jeden nad drugim podczas dodawania, pamiętaj, że obiekt FlowLayoutPanel jest zaznaczony przed dodaniem przycisków. Mimo że wcześniej stwierdzono, że każda komórka może zawierać tylko jeden formant, skrajna prawa komórka TableLayoutPanel ma cztery formanty przycisków. Jest to spowodowane możesz umieścić formant w komórce, która zawiera inne kontrolki. Tego rodzaju kontrolę nazywamy kontenerem, a FlowLayoutPanel jest kontenerem.  
  
### <a name="to-add-buttons"></a>Aby dodać przyciski  
  
1. Wybierz nowy FlowLayoutPanel, który został dodany. Przejdź do **wspólnych formantów** w przyborniku i kliknij dwukrotnie **przycisk** element, aby dodać formant przycisku o nazwie **button1** do obiektu FlowLayoutPanel. Powtarzaj, aby dodać inny przycisk. IDE ustala, że istnieje już przycisk o nazwie **button1** i wywołuje następny **button2**.  
  
2. Zazwyczaj dodajesz inne przyciski korzystając z przybornika. Tym razem wybierz **button2**, a następnie na pasku menu wybierz **Edytuj**, **kopiowania** (lub naciśnij klawisze Ctrl + C). Na pasku menu wybierz **Edytuj**, **Wklej** (lub naciśnij klawisze Ctrl + V) Wklej przycisku. Teraz Wklej ponownie. IDE dodało **button3** i **button4** do FlowLayoutPanel.  
  
    > [!NOTE]
    > Można skopiować i wkleić dowolny formant. IDE nazywa i umieszcza nowe formanty w sposób logiczny. Po wklejeniu formantu do kontenera środowisko IDE wybiera następne logiczne miejsce dla umieszczenia.  
  
3. Wybierz pierwszy przycisk i ustaw jego **tekstu** właściwości **Pokaż obraz**. Następnie ustaw **tekstu** właściwości kolejnych trzech przycisków **Wyczyść obraz**, **Ustaw kolor tła**, i **Zamknij**.  
  
4. Następnym krokiem jest wielkości przycisków i rozmieszczenie ich, aby były wyrównane do prawej strony panelu. Wybierz FlowLayoutPanel i przyjrzyj się jego **FlowDirection** właściwości. Go zmienić, dzięki czemu jest równa **RightToLeft**. Jak najszybciej zrobisz, przyciski powinny wyrównać się do prawej strony komórki i odwrócić kolejność tak, aby **Pokaż obraz** przycisk po prawej.  
  
    > [!NOTE]
    > Jeśli przyciski są nadal w złej kolejności, można przeciągnąć przyciski w granicach obiektu FlowLayoutPanel w celu ich rozmieszczenia w dowolnej kolejności. Można wybrać przycisk i przeciągnij go w lewo lub w prawo.  
  
5. Wybierz **Zamknij** przycisk, aby go zaznaczyć. Naciśnij i przytrzymaj klawisz CTRL i wybierz pozostałe trzy przyciski są wszystkie zaznaczone. Gdy zaznaczone są wszystkie przyciski, przejdź do **właściwości** okna i przewiń do **AutoSize** właściwości. Ta właściwość zawiera informacje rozmiar przycisku automatycznie dopasuje wszystkich swoich tekstów. Ustaw ją na **true**. Przyciski powinny teraz być wielkość i być w odpowiedniej kolejności. (Tak długo, jak wszystkie cztery przyciski są zaznaczone, można zmienić wszystkie cztery **AutoSize** właściwości w tym samym czasie.) Na poniższej ilustracji przedstawiono cztery przyciski.  
  
     ![Obraz podglądu z czterema przyciskami](../ide/media/express-autosize.png "Express_AutoSize")  
Przeglądarka obrazów z czterema przyciskami  
  
6. Teraz uruchom program ponownie, aby zobaczyć układem formularza. Wybieranie przycisków i pola wyboru jeszcze nic nie robi, ale wkrótce będą one działać.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [krok 6: Nazw kontrolkom przycisków](../ide/step-6-name-your-button-controls.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4: Określić układ formularza z formantem TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
