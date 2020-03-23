---
title: 'Krok 1: Tworzenie projektu i dodawanie etykiet do formularza'
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bf904fca84fba88e81306ff91add6c2156b4544
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579446"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1: Tworzenie projektu i dodawanie etykiet do formularza

Jako pierwsze kroki w tworzeniu tego quizu, należy utworzyć projekt i dodać etykiety, przycisk i inne formanty do formularza. Można również ustawić właściwości dla każdego formantu, który można dodać. Projekt będzie zawierał formularz, formanty i (w dalszej części samouczka) kod. Przycisk rozpoczyna quiz, etykiety pokazują problemy z quizem, a inne elementy sterujące pokazują odpowiedzi na quiz i czas, który pozostaje do zakończenia quizu.

> [!NOTE]
> Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-project-for-a-form"></a>Aby utworzyć projekt dla formularza

::: moniker range="vs-2017"

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. Wybierz pozycję **Visual C#** lub **Visual Basic** po lewej stronie okna dialogowego Nowy **projekt,** a następnie wybierz pozycję **Pulpit systemu Windows**.

1. Na liście szablonów wybierz szablon **aplikacji Windows Forms App (.NET Framework),** nazwij go *MathQuiz*, a następnie wybierz przycisk **OK.**

    Zostanie wyświetlony formularz o nazwie *Form1.cs* lub *Form1.vb,* w zależności od wybranego języka programowania.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji Windows Forms App (.NET Framework),** użyj Instalatora programu Visual Studio, aby zainstalować obciążenie **programowe .NET dla deweloperów pulpitu.**<br/><br/>![Obciążenie programistyczne pulpitu .NET w Instalatorze programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz stronę [Instalowanie programu Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *formularze systemu Windows* w polu wyszukiwania. Następnie wybierz pozycję **Pulpit** z listy **Typu projektu.**

   Po zastosowaniu filtru **typu projektu** wybierz szablon aplikacji Windows Forms **App (.NET Framework)** dla języka C# lub Visual Basic, a następnie wybierz pozycję **Dalej**.

   ![Wybierz szablon C# lub Visual Basic dla aplikacji Windows Forms App (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli nie jest wyświetlany szablon **aplikacji Windows Forms App (.NET Framework),** można go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalatorze programu Visual Studio wybierz zadanie **tworzenia pulpitu .NET.**
   >
   > ![Obciążenie rdzenia .NET w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie.

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MathQuiz* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Aby ustawić właściwości formularza

1. W programie Visual Studio wybierz formularz *(Form1.cs* lub *Form1.vb*, w zależności od języka programowania), a następnie zmień jego **właściwość Tekst** na **Quiz matematyczny.**

     Okno **Właściwości** zawiera właściwości formularza.

1. Zmień rozmiar formularza na 500 pikseli szerokości na 400 pikseli wysokości.

     Można zmienić rozmiar formularza, przeciągając jego krawędzie, aż w lewym dolnym rogu zintegrowanego środowiska programistycznego (IDE) pojawi się odpowiedni rozmiar. Alternatywnie można zmienić wartości **Size** właściwości.

1. Zmień wartość właściwości **FormBorderStyle** na **Fixed3D**i ustaw właściwość **MaximizeBox** na **False**.

     Te wartości uniemożliwiają uczestnikom quizu zmiana rozmiaru formularza.

## <a name="to-create-the-time-remaining-box"></a>Aby utworzyć pole pozostały czas

1. Dodaj <xref:System.Windows.Forms.Label> formant z **przybornika**, a następnie ustaw wartość jego **właściwości (Nazwa)** na **timeLabel**.

     Ta etykieta stanie się polem w prawym górnym rogu, które pokazuje liczbę sekund, które pozostały w quizie.

2. Zmień właściwość **Autosize** na **False,** aby można było zmienić rozmiar tego pola.

3. Zmień **właściwość BorderStyle** na **FixedSingle,** aby narysować linię wokół pola.

4. Ustaw **size** właściwość **na 200, 30**.

5. Przenieś etykietę do prawego górnego rogu formularza, gdzie pojawią się niebieskie linie dystansowe.

     Te wiersze ułatwiają wyrównywanie formantów w formularzu.

6. W oknie **Właściwości** wybierz właściwość **Text,** a następnie wybierz klawisz **Backspace,** aby wyczyścić jego wartość.

7. Wybierz znak plus**+**( ) obok **Font** właściwości, a następnie zmień wartość **Size** właściwości na **15.75**.

     Można zmienić kilka właściwości czcionki, jak pokazano na poniższym zrzucie ekranu.

     ![Okno Właściwości z rozmiarem czcionki](../ide/media/express_setfontsize.png)

8. Dodaj kolejny formant Etykiety z **przybornika,** a następnie ustaw jego rozmiar czcionki na **15.75**.

9. Ustaw **właściwość Tekst** na **Pozostały czas**.

10. Przenieś etykietę tak, aby była liniami po lewej stronie etykiety **timeLabel.**

### <a name="to-add-controls-for-the-addition-problems"></a>Aby dodać kontrolki problemów z dodawaniem

1. Dodaj formant Label z **przybornika**, a następnie ustaw jego **text** **właściwości?** (znak zapytania).

2. Ustaw właściwość **AutoSize** na **False**.

3. Ustaw **size** właściwość na **60, 50**.

4. Ustaw rozmiar czcionki na **18**.

5. Ustaw **właściwość TextAlign** na **MiddleCenter**.

6. Ustaw **Location właściwość** **50, 75,** aby umieścić formant w formularzu.

7. Ustaw właściwość **(Nazwa)** na **plusLeftLabel**.

8. Wybierz etykietę **plusLeftLabel,** a następnie wybierz klawisze **Ctrl**+**C** lub **Kopiuj** w menu **Edycja.**

9. Wklej etykietę trzy razy, wybierając klawisze **Ctrl**+**V** lub **Wklej** w menu **Edycja.**

10. Rozmieść trzy nowe etykiety tak, aby były w rzędzie po prawej stronie etykiety **plusLeftLabel.**

     Można użyć linii dystansowych, aby rozmieścić je i wyrównać.

11. Ustaw wartość właściwości **Text** drugiej etykiety **+** na (znak plus).

12. Ustaw wartość właściwości **(Name)** trzeciej etykiety na **plusRightLabel**.

13. Ustaw wartość właściwości **Text** czwartej etykiety **=** na (znak równości).

14. Dodaj <xref:System.Windows.Forms.NumericUpDown> kontrolkę z **przybornika,** ustaw jego rozmiar czcionki na **18**i ustaw jego szerokość na **100**.

     Dowiesz się więcej o tego rodzaju kontroli później.

15. Ujednolić formant NumericUpDown z formantami Label dla problemu z dodawaniem.

16. Zmień wartość właściwości **(Nazwa)** formantu NumericUpDown na **sumę**.

     Utworzono pierwszy wiersz, jak pokazano na poniższej ilustracji.

     ![Pierwszy rząd quizu matematycznego](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Aby dodać formanty problemów z odejmowaniem, mnożeniem i dzieleniem

1. Skopiuj wszystkie pięć formantów dla problemu z dodawaniem (cztery formanty Label i Formant NumericUpDown), a następnie wklej je.

     Formularz zawiera pięć nowych formantów, które są nadal zaznaczone.

2. Przenieś wszystkie formanty na miejsce, tak aby były one w kolejce poniżej formantów dodawania.

     Można użyć linii dystansowych, aby zapewnić wystarczającą odległość między dwoma wierszami.

3. Zmień wartość **Text** właściwości dla drugiej **-** etykiety na (znak minus).

4. Nazwij pierwszą etykietę znaku zapytania **minusLeftLabel**.

5. Nazwij drugą etykietę znaku zapytania **minusRightLabel**.

6. Nazwij **różnicę**formantu NumericUpDown .

7. Wklej pięć formantów jeszcze dwa razy.

8. W trzecim wierszu nazwij pierwszą etykietę **razyLeftLabel**, zmień właściwość **Text** drugiej etykiety na **×** (znak mnożenia), nazwij trzecią etykietę **timesRightLabel**i nazwij **produkt**kontrolny NumericUpDown .

9. W czwartym wierszu nazwij pierwszą etykietę **podzielonąLeftLabel**, zmień właściwość **Text** drugiej etykiety na **÷** (znak podziału), nazwij trzecią etykietę **podzielonąUprawna,** i nazwij **iloraz formantu**NumericUpDown .

    > [!NOTE]
    > Możesz skopiować znak mnożenia × i znak podziału ÷ z tego samouczka i wkleić je do formularza.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Aby dodać przycisk start i ustawić kolejność indeksów kart

1. Dodaj <xref:System.Windows.Forms.Button> formant z **przybornika**, a następnie ustaw jego **właściwość (Nazwa),** aby **uruchomićButton**.

2. Ustaw **text** właściwość, aby **rozpocząć quiz**.

3. Ustaw rozmiar czcionki na **14**.

4. Ustaw właściwość **Autosize** na **True**, co powoduje, że rozmiar przycisku powoduje, że rozmiar jest automatycznie pasowy do tekstu.

5. Wyśrodkuj przycisk u dołu formularza.

6. Ustaw wartość właściwości **TabIndex** dla formantu **startButton** na **1**.

    > [!NOTE]
    > **Właściwość TabIndex** ustawia kolejność formantów, gdy osoba biorąca quiz wybierze klawisz **Tab.** Aby zobaczyć, jak to działa, otwórz dowolne okno dialogowe (na przykład na pasku menu wybierz pozycję**Otwórz** **plik),** > a następnie wybierz klawisz **Tab** kilka razy. Obserwuj, jak kursor przechodzi od sterowania do sterowania za każdym razem, gdy wybierzesz klawisz **Tab.** Programista zdecydował kolejność podczas tworzenia tego formularza.

7. Ustaw wartość właściwości **TabIndex** dla formantu Suma NumericUpDown na **2,** dla kontroli różnicy na **3,** dla formantu produktu na **4**i dla formantu ilorazu na **5**.

     Formularz powinien wyglądać podobnie do poniższego zrzutu ekranu.

     ![Wstępny formularz quizu matematycznego](../ide/media/express_formlaidout.png)

8. Aby sprawdzić, czy właściwość **TabIndex** działa zgodnie z oczekiwaniami, zapisz i uruchom program, wybierając klawisz **F5** lub wybierając **debugowanie** > **start debugowania** na pasku menu, a następnie wybierz klawisz **Tab** kilka razy.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 2: Tworzenie losowego problemu z dodawaniem](../ide/step-2-create-a-random-addition-problem.md)**.

- Aby powrócić do tematu przeglądu, zobacz [Samouczek 2: Tworzenie quizu matematycznego z czasem](../ide/tutorial-2-create-a-timed-math-quiz.md).
