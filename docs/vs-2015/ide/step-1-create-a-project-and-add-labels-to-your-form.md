---
title: Krok 1. Tworzenie projektu i dodawanie etykiet do formularza | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e58471c1676ce67e96ef2c325f5ec461f54cfc9c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441984"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1. Tworzenie projektu i dodawanie etykiet do formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jako pierwsze kroki w projektowaniu tego quizu tworzysz projekt i dodać etykiety, przycisk i inne formanty do formularza. Można również ustawić właściwości dla każdego dodawanego formantu. Projekt będzie zawierać formularz, formanty oraz (później w samouczku) kod. Przycisk uruchamia quiz, etykiety pokazują problemy quizu, a pozostałe formanty pokazują odpowiedzi do quizu oraz czas pozostały do jego zakończenia.  
  
> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz Quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-create-a-project-and-set-properties-for-a-form"></a>Aby utworzyć projekt i ustawić właściwości dla formularza  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. W **zainstalowane szablony** , wybierz opcję **C#** lub **języka Visual Basic**.  
  
3. Z listy szablonów wybierz **aplikacja interfejsu Windows Forms** szablonu, nadaj jej nazwę **Math Quiz**, a następnie wybierz **OK** przycisku.  
  
     Formularz, który nosi nazwę **Form1.cs** lub **Form1.vb** pojawia się w zależności od języka programowania, który został wybrany.  
  
4. Wybierz formularz, a następnie zmień jego **tekstu** właściwości **Math Quiz**.  
  
     **Właściwości** okno zawiera właściwości dla formularza.  
  
5. Zmień rozmiar formularza na 500 pikseli szerokości i 400 pikseli wysokości.  
  
     Można zmienić rozmiar formularza, przeciągając jego krawędzie, aż pojawi się prawidłowy rozmiar, w lewym dolnym rogu zintegrowanego środowiska programistycznego (IDE). Alternatywnie, można zmienić wartości **rozmiar** właściwości.  
  
6. Zmień wartość właściwości **FormBorderStyle** właściwości **Fixed3D**i ustaw **MaximizeBox** właściwości **False**.  
  
     Te wartości uniemożliwiają uczestnikom quizu zmianę rozmiaru formularza.  
  
### <a name="to-create-the-time-remaining-box"></a>Aby utworzyć pole pozostałego czasu  
  
1. Dodaj **etykiety** sterowania z przybornika, a następnie ustaw wartość jego **(nazwa)** właściwość `timeLabel`.  
  
     Ta etykieta stanie się polem w prawym górnym rogu, który pokazuje liczbę sekund pozostałych do końca quizu.  
  
2. Zmiana **AutoSize** właściwości **False** tak, aby zmienić rozmiar pola.  
  
3. Zmiana **BorderStyle** właściwości **FixedSingle** Aby narysować linię wokół pola.  
  
4. Ustaw **rozmiar** właściwości **200, 30**.  
  
5. Przenieś etykietę do prawego górnego rogu formularza, gdzie pojawią się niebieskie linie rozdzielacza.  
  
     Te wiersze ułatwiają wyrównywanie formantów na formularzu.  
  
6. W **właściwości** oknie Wybierz **tekstu** właściwości, a następnie naciśnij klawisz Backspace, aby wyczyścić jej wartość.  
  
7. Wybierz znak plus (+) obok **czcionki** właściwości, a następnie zmień wartość **rozmiar** właściwości **15,75**.  
  
     Możesz zmienić kilka właściwości czcionki, jak przedstawiono na poniższym obrazie.  
  
     ![Okno właściwości pokazujące rozmiar czcionki](../ide/media/express-setfontsize.png "Express_setFontSize")  
Okno właściwości, w którym jest widoczny rozmiar czcionki  
  
8. Dodaj kolejną **etykiety** sterowania z przybornika, a następnie ustaw jego rozmiar czcionki na **15,75**.  
  
9. Ustaw **tekstu** właściwości **Pozostało**.  
  
10. Przenieś etykietę tak, aby go wyrównana tuż po lewej stronie **timeLabel** etykiety.  
  
### <a name="to-add-controls-for-the-addition-problems"></a>Aby dodać formanty do problemów dodawania  
  
1. Dodaj **etykiety** sterowania z przybornika, a następnie ustaw jego **tekstu** właściwość **?** (znak zapytania).  
  
2. Ustaw **AutoSize** właściwości **False**.  
  
3. Ustaw **rozmiar** właściwości **60, 50**.  
  
4. Ustaw rozmiar czcionki na **18**.  
  
5. Ustaw **TextAlign** właściwości **MiddleCenter**.  
  
6. Ustaw **lokalizacji** właściwości **50, 75** położenie formantu w formularzu.  
  
7. Ustaw **(nazwa)** właściwości **plusLeftLabel**.  
  
8. Wybierz **plusLeftLabel** etykiety, a następnie wybierz klawisze Ctrl + C lub **kopiowania** na **Edytuj** menu.  
  
9. Wklej etykietę trzy razy, wybierając klawisze Ctrl + V lub **Wklej** na **Edytuj** menu.  
  
10. Rozmieść trzy nowe etykiety, tak aby były w wierszu z prawej strony **plusLeftLabel** etykiety.  
  
     Aby rozmieścić je i wiersz w górę, można użyć linii rozdzielacza.  
  
11. Ustaw wartość drugiej etykiety **tekstu** właściwości **+** (znak plus).  
  
12. Ustaw wartość trzeciej etykiety **(nazwa)** właściwości **plusRightLabel**.  
  
13. Ustaw wartość czwartej etykiety **tekstu** właściwości **=** (znak równości).  
  
14. Dodaj **NumericUpDown** z przybornika, ustaw jego rozmiar czcionki **18**i ustaw jego szerokość na **100**.  
  
     Dowiesz się więcej na temat tego rodzaju formantu później.  
  
15. Wiersz w górę **NumericUpDown** kontrolki z formantami etykiet dla problemu dodawania.  
  
16. Zmień wartość właściwości **(nazwa)** właściwość **NumericUpDown** kontrolę **suma**.  
  
     Utworzyłeś pierwszy wiersz, jak przedstawiono na poniższym obrazie.  
  
     ![Pierwszy wiersz kwizu matematycznego z limitem](../ide/media/express-firstrow.png "Express_firstRow")  
Pierwszy wiersz kwizu matematycznego z limitem  
  
### <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Aby dodać formanty do problemów odejmowania, mnożenia i dzielenia  
  
1. Skopiuj wszystkie pięć formantów dla problemu dodawania (cztery formanty etykiet i formant NumericUpDown), a następnie wklej je.  
  
     Formularz zawiera pięć nowych formantów, które nadal będą zaznaczone.  
  
2. Przenieś wszystkie formanty w miejscu, tak, aby były wyrównane poniżej formantów dodatku.  
  
     Aby zapewnić wystarczającą odległość między dwoma wierszami, można użyć linii rozdzielacza.  
  
3. Zmień wartość właściwości **tekstu** właściwość drugiej etykiety na **—** (znak minusa).  
  
4. Nadaj pierwszej etykiecie znaku zapytania **minusLeftLabel**.  
  
5. Nadaj drugiej etykiecie znaku zapytania **minusRightLabel**.  
  
6. Nazwa **NumericUpDown** kontroli **różnica**.  
  
7. Wklej pięć formantów jeszcze dwa razy.  
  
8. W trzecim rzędzie, nazwij pierwszą etykietę **timesLeftLabel**, zmień drugiej etykiety **tekstu** właściwości **×** (znak mnożenia), nazwij trzecią etykietę **timesRightLabel**i nazwij formant NumericUpDown **produktu**.  
  
9. Na czwartym wierszu, nazwij pierwszą etykietę **dividedLeftLabel**, zmień drugiej etykiety **tekstu** właściwości **÷** (znak dzielenia), nazwij trzecią etykietę  **dividedRightLabel**i nazwij formant NumericUpDown **iloraz**.  
  
    > [!NOTE]
    > Można skopiować z tego samouczka × znak mnożenia i ÷ znak dzielenia i wklej je do formularza.  
  
### <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Aby dodać przycisk start i ustawić kolejność kolejność tabulacji  
  
1. Dodaj **przycisk** sterowania z przybornika, a następnie ustaw jego **(nazwa)** właściwości **startButton**.  
  
2. Ustaw **tekstu** właściwości **Uruchom quiz**.  
  
3. Ustaw rozmiar czcionki na **14**.  
  
4. Ustaw **AutoSize** właściwości **True**, co powoduje, że rozmiar przycisku automatycznie dopasuje się do tekstu.  
  
5. Wyśrodkuj przycisk w dolnej części formularza.  
  
6. Ustaw wartość **TabIndex** właściwość **startButton** kontrolę **1**.  
  
    > [!NOTE]
    > **TabIndex** właściwość ustawia kolejność formantów, gdy uczestnik quizu wybiera klawisz Tab. Aby zobaczyć, jak to działa, otwórz dowolne okno dialogowe (na przykład, na pasku menu należy wybrać **pliku**, **Otwórz**), a następnie wybierz klawisz Tab kilka razy. Obejrzyj, jak Twoja kursor przesuwa się między formantami każdorazowo, naciśnij klawisz Tab. Programista zdecydował o kolejności podczas tworzenia tego formularza.  
  
7. Ustaw wartość **TabIndex** właściwość sumy numericupdown na **2**, dla formantu różnicy na **3**, dla formantu iloczynu na **4**, a dla formantu ilorazu na **5**.  
  
     Formularz powinien wyglądać podobnie do poniższej ilustracji.  
  
     ![Początkowy formularz quizu matematycznego](../ide/media/express-formlaidout.png "Express_FormLaidOut")  
Wstępny formularz quizu matematycznego  
  
8. Aby sprawdzić, czy **TabIndex** właściwości działa zgodnie z oczekiwaniami, Zapisz i uruchom program, wybierając klawisz F5 lub wybierając **debugowania**, **Rozpocznij debugowanie** na pasku menu a następnie naciśnij klawisz Tab kilka razy.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [krok 2: Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md).  
  
- Aby powrócić do tematu przeglądu, zobacz [samouczek 2: Utwórz Quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).
