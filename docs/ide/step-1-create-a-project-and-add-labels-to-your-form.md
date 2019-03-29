---
title: Krok 1. Tworzenie projektu i dodawanie etykiet do formularza
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d077cd549b5bef703229b2c43f4ce36d9735d512
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647404"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1. Tworzenie projektu i dodawanie etykiet do formularza

Jako pierwsze kroki w projektowaniu tego quizu tworzysz projekt i dodać etykiety, przycisk i inne formanty do formularza. Można również ustawić właściwości dla każdego dodawanego formantu. Projekt będzie zawierać formularz, formanty oraz (później w samouczku) kod. Przycisk uruchamia quiz, etykiety pokazują problemy quizu, a pozostałe formanty pokazują odpowiedzi do quizu oraz czas pozostały do jego zakończenia.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-project-and-set-properties-for-a-form"></a>Aby utworzyć projekt i ustawić właściwości dla formularza

::: moniker range="vs-2017"

1.  Na pasku menu wybierz **pliku** > **New** > **projektu**.

1.  W **zainstalowane szablony** , wybierz opcję **C#** lub **języka Visual Basic**.

1.  Z listy szablonów wybierz **aplikacja interfejsu Windows Forms** szablonu, nadaj jej nazwę **MathQuiz**, a następnie wybierz **OK** przycisku.

     Formularz, który nosi nazwę *Form1.cs* lub *Form1.vb* pojawia się w zależności od języka programowania, który został wybrany.

::: moniker-end

::: moniker range="vs-2019"

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

1. Wybierz pozycję w polu wyszukiwania wpisz "WPF" **aplikacja WPF (.NET Framework)**, a następnie wybierz **dalej**.

   (Jeśli nie widzisz **aplikacja WPF (.NET Framework)** szablon, użyj Instalatora programu Visual Studio, aby zainstalować **programowanie aplikacji klasycznych dla platformy .NET** obciążenia.)

1. Nazwij projekt, **MathQuiz**i wybierz polecenie **Create**

::: moniker-end

1.  Wybierz formularz, a następnie zmień jego **tekstu** właściwości **Math Quiz**.

     **Właściwości** okno zawiera właściwości dla formularza.

1.  Zmień rozmiar formularza na 500 pikseli szerokości i 400 pikseli wysokości.

     Można zmienić rozmiar formularza, przeciągając jego krawędzie, aż pojawi się prawidłowy rozmiar, w lewym dolnym rogu zintegrowanego środowiska programistycznego (IDE). Alternatywnie, można zmienić wartości **rozmiar** właściwości.

1.  Zmień wartość właściwości **FormBorderStyle** właściwości **Fixed3D**i ustaw **MaximizeBox** właściwości **False**.

     Te wartości uniemożliwiają uczestnikom quizu zmianę rozmiaru formularza.

## <a name="to-create-the-time-remaining-box"></a>Aby utworzyć okno pozostały czas

1.  Dodaj <xref:System.Windows.Forms.Label> z kontrolować **przybornika**, a następnie ustaw wartość jego **(nazwa)** właściwości **timeLabel**.

     Ta etykieta stanie się polem w prawym górnym rogu, który pokazuje liczbę sekund pozostałych do końca quizu.

2.  Zmiana **AutoSize** właściwości **False** tak, aby zmienić rozmiar pola.

3.  Zmiana **BorderStyle** właściwości **FixedSingle** Aby narysować linię wokół pola.

4.  Ustaw **rozmiar** właściwości **200, 30**.

5.  Przenieś etykietę do prawego górnego rogu formularza, gdzie pojawią się niebieskie linie rozdzielacza.

     Te wiersze ułatwiają wyrównywanie formantów na formularzu.

6.  W **właściwości** oknie Wybierz **tekstu** właściwości, a następnie wybierz **Backspace** klawisz, aby wyczyścić jej wartość.

7.  Wybierz znak plus (**+**) obok pozycji **czcionki** właściwości, a następnie zmień wartość **rozmiar** właściwości **15,75**.

     Możesz zmienić kilka właściwości czcionki, jak przedstawiono na poniższym obrazie.

     ![Okno właściwości, w którym jest widoczny rozmiar czcionki](../ide/media/express_setfontsize.png)

8.  Dodaj inną kontrolkę etykiety z **przybornika**, a następnie ustaw jego rozmiar czcionki na **15,75**.

9. Ustaw **tekstu** właściwości **Pozostało**.

10. Przenieś etykietę tak, aby go wyrównana tuż po lewej stronie **timeLabel** etykiety.

### <a name="to-add-controls-for-the-addition-problems"></a>Aby dodać formanty do problemów dodawania

1.  Dodaj kontrolkę etykieta z **przybornika**, a następnie ustaw jego **tekstu** właściwość **?** (znak zapytania).

2.  Ustaw **AutoSize** właściwości **False**.

3.  Ustaw **rozmiar** właściwości **60, 50**.

4.  Ustaw rozmiar czcionki na **18**.

5.  Ustaw **TextAlign** właściwości **MiddleCenter**.

6.  Ustaw **lokalizacji** właściwości **50, 75** położenie formantu w formularzu.

7.  Ustaw **(nazwa)** właściwości **plusLeftLabel**.

8.  Wybierz **plusLeftLabel** etykiety, a następnie wybierz opcję **Ctrl**+**C** kluczy lub **kopiowania** na  **Edytuj** menu.

9. Wklej etykietę trzy razy, wybierając opcję **Ctrl**+**V** kluczy lub **Wklej** na **Edytuj** menu.

10. Rozmieść trzy nowe etykiety, tak aby były w wierszu z prawej strony **plusLeftLabel** etykiety.

     Aby rozmieścić je i wiersz w górę, można użyć linii rozdzielacza.

11. Ustaw wartość drugiej etykiety **tekstu** właściwości **+** (znak plus).

12. Ustaw wartość trzeciej etykiety **(nazwa)** właściwości **plusRightLabel**.

13. Ustaw wartość czwartej etykiety **tekstu** właściwości **=** (znak równości).

14. Dodaj <xref:System.Windows.Forms.NumericUpDown> z kontrolować **przybornika**, ustaw jego rozmiar czcionki na **18**i ustaw jego szerokość na **100**.

     Dowiesz się więcej na temat tego rodzaju formantu później.

15. Wiersz w górę formant NumericUpDown z formantami etykiet dla problemu dodawania.

16. Zmień wartość właściwości **(nazwa)** właściwości dla formantu NumericUpDown, ma **suma**.

     Utworzyłeś pierwszy wiersz, jak przedstawiono na poniższym obrazie.

     ![Pierwszy wiersz kwizu matematycznego z limitem](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Aby dodać formanty do problemów odejmowania, mnożenia i dzielenia

1.  Skopiuj wszystkie pięć formantów dla problemu dodawania (cztery formanty etykiet i formant NumericUpDown), a następnie wklej je.

     Formularz zawiera pięć nowych formantów, które nadal będą zaznaczone.

2.  Przenieś wszystkie formanty w miejscu, tak, aby były wyrównane poniżej formantów dodatku.

     Aby zapewnić wystarczającą odległość między dwoma wierszami, można użyć linii rozdzielacza.

3.  Zmień wartość właściwości **tekstu** właściwość drugiej etykiety na **-** (znak minusa).

4.  Nadaj pierwszej etykiecie znaku zapytania **minusLeftLabel**.

5.  Nadaj drugiej etykiecie znaku zapytania **minusRightLabel**.

6.  Nazwij formant NumericUpDown **różnica**.

7.  Wklej pięć formantów jeszcze dwa razy.

8.  W trzecim rzędzie, nazwij pierwszą etykietę **timesLeftLabel**, zmień drugiej etykiety **tekstu** właściwości **×** (znak mnożenia), nazwij trzecią etykietę **timesRightLabel**i nazwij formant NumericUpDown **produktu**.

9. Na czwartym wierszu, nazwij pierwszą etykietę **dividedLeftLabel**, zmień drugiej etykiety **tekstu** właściwości **÷** (znak dzielenia), nazwij trzecią etykietę  **dividedRightLabel**i nazwij formant NumericUpDown **iloraz**.

    > [!NOTE]
    > Można skopiować z tego samouczka × znak mnożenia i ÷ znak dzielenia i wklej je do formularza.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Aby dodać przycisk start i ustawić kolejność kolejność tabulacji

1.  Dodaj <xref:System.Windows.Forms.Button> kontrolować z **przybornika**, a następnie ustaw jego **(nazwa)** właściwości **startButton**.

2.  Ustaw **tekstu** właściwości **Uruchom quiz**.

3.  Ustaw rozmiar czcionki na **14**.

4.  Ustaw **AutoSize** właściwości **True**, co powoduje, że rozmiar przycisku automatycznie dopasuje się do tekstu.

5.  Wyśrodkuj przycisk w dolnej części formularza.

6.  Ustaw wartość **TabIndex** właściwość **startButton** kontrolę **1**.

    > [!NOTE]
    > **TabIndex** właściwość ustawia kolejność formantów, gdy uczestnik quizu wybierze **kartę** klucza. Aby zobaczyć, jak to działa, otwórz dowolne okno dialogowe (na przykład, na pasku menu należy wybrać **pliku** > **Otwórz**), a następnie wybierz **kartę** klucz kilka razy. Obejrzyj, jak Twoja kursor przesuwa się między formantami każdorazowo wybranie **kartę** klucza. Programista zdecydował o kolejności podczas tworzenia tego formularza.

7.  Ustaw wartość **TabIndex** właściwość sumy numericupdown na **2**, dla formantu różnicy na **3**, dla formantu iloczynu na **4**, a dla formantu ilorazu na **5**.

     Formularz powinien wyglądać podobnie do poniższej ilustracji.

     ![Wstępny formularz quizu matematycznego](../ide/media/express_formlaidout.png)

8.  Aby sprawdzić, czy **TabIndex** właściwości działa jak oczekujesz, Zapisz i uruchom program, wybierając **F5** klucza lub przez wybranie **debugowania**  >  **Rozpocznij debugowanie** menu paska, a następnie wybierz **kartę** klucz kilka razy.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 2: Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md).

-   Aby powrócić do tematu przeglądu, zobacz [samouczek 2: Utwórz quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).
