---
title: Krok 1. Tworzenie projektu i dodawanie etykiet do formularza
description: Dowiedz się, jak utworzyć projekt, dodać etykiety, przycisk i inne kontrolki do formularza, a następnie ustawić właściwości dla każdej dodawanej kontrolki.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7597b97a93b2e602a3166eb60b4055082ed7675f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951020"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1. Tworzenie projektu i dodawanie etykiet do formularza

Pierwszym etapem tworzenia tego quizu jest utworzenie projektu i dodanie etykiet, przycisku i innych kontrolek do formularza. Należy również ustawić właściwości dla każdej dodawanej kontrolki. Projekt będzie zawierać formularz, formanty i (w dalszej części samouczka). Przycisk uruchamia quiz, etykiety pokazują problemy z quizem, a inne kontrolki wyświetlają odpowiedzi quizu i czas, który pozostanie do końca quizu.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-project-for-a-form"></a>Aby utworzyć projekt dla formularza

::: moniker range="vs-2017"

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. Wybierz opcję **Visual C#** lub **Visual Basic** po lewej stronie okna dialogowego **Nowy projekt** , a następnie wybierz pozycję **Windows Desktop**.

1. Na liście szablonów wybierz szablon **aplikacja Windows Forms (.NET Framework)** , nadaj mu nazwę *MathQuiz*, a następnie wybierz przycisk **OK** .

    Zostanie wyświetlony formularz o nazwie *Form1.cs* lub *Form1. vb* , w zależności od wybranego języka programowania.

   > [!NOTE]
   > Jeśli szablon **aplikacji Windows Forms (.NET Framework)** nie jest widoczny, użyj Instalator programu Visual Studio, aby zainstalować obciążenie **programistyczne dla programu .NET Desktop** .<br/><br/>![Obciążenie Programowanie aplikacji klasycznych platformy .NET w Instalator programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz stronę [Instalowanie programu Visual Studio](../install/install-visual-studio.md) .

::: moniker-end

::: moniker range="vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wprowadź lub wpisz *Windows Forms* w polu wyszukiwania. Następnie wybierz pozycję **pulpit** z listy **Typ projektu** .

   Po zastosowaniu filtru **Typ projektu** wybierz szablon **aplikacja Windows Forms (.NET Framework)** dla języka C# lub Visual Basic, a następnie wybierz przycisk **dalej**.

   ![Wybierz szablon C# lub Visual Basic dla aplikacji Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli szablon **aplikacji Windows Forms (.NET Framework)** nie jest wyświetlany, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** .
   >
   > ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie.

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MathQuiz* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Aby ustawić właściwości formularza

1. W programie Visual Studio wybierz formularz ( *Form1.cs* lub *Form1. vb*, w zależności od języka programowania), a następnie zmień jego właściwość **Text** na **Quiz matematyczny**.

     Okno **Właściwości** zawiera właściwości dla formularza.

1. Zmień rozmiar formularza na 500 pikseli szerokości o 400 pikseli wysokości.

     Można zmienić rozmiar formularza, przeciągając jego krawędzie do momentu pojawienia się w lewym dolnym rogu zintegrowanego środowiska programistycznego (IDE). Alternatywnie można zmienić wartości właściwości **size** .

1. Zmień wartość właściwości **FormBorderStyle** na **Fixed3D** i ustaw właściwość **MaximizeBox** na **false**.

     Te wartości uniemożliwiają uczestnikomom quizu zmianę rozmiarów formularza.

## <a name="to-create-the-time-remaining-box"></a>Aby utworzyć pole pozostało czasu

1. Dodaj <xref:System.Windows.Forms.Label> kontrolkę z **przybornika**, a następnie ustaw wartość właściwości **(Name)** na **timeLabel**.

     Ta etykieta zostanie umieszczony w prawym górnym rogu, która pokazuje liczbę sekund, które pozostaną w quizie.

2. Zmień właściwość **AutoSize** na **false** , aby można było zmienić rozmiar pola.

3. Zmień właściwość **BorderStyle** na **FixedSingle** , aby narysować linię wokół pola.

4. Ustaw właściwość **size** na **200, 30**.

5. Przenieś etykietę do prawego górnego rogu formularza, gdzie pojawią się niebieskie linie odstępu.

     Te wiersze ułatwiają wyrównywanie kontrolek w formularzu.

6. W oknie **Właściwości** wybierz właściwość **tekst** , a następnie wybierz klawisz **Backspace** , aby wyczyścić jego wartość.

7. Wybierz znak plus ( **+** ) obok właściwości **Font** , a następnie zmień wartość właściwości **size** na **15,75**.

     Można zmienić kilka właściwości czcionki, jak pokazano na poniższym zrzucie ekranu.

     ![okno Właściwości pokazywanie rozmiaru czcionki](../ide/media/express_setfontsize.png)

8. Dodaj kolejną kontrolkę etykieta z **przybornika**, a następnie ustaw jej rozmiar czcionki na **15,75**.

9. Ustaw właściwość **Text** na wartość **Time Left**.

10. Przenieś etykietę tak, aby była wierszem po lewej stronie etykiety **timeLabel** .

### <a name="to-add-controls-for-the-addition-problems"></a>Aby dodać kontrolki dla problemów dodatkowych

1. Dodaj kontrolkę etykieta z **przybornika**, a następnie ustaw jej właściwość **Text** na **?** (znak zapytania).

2. Ustaw właściwość **AutoSize** na **false**.

3. Ustaw właściwość **size** na **60, 50**.

4. Ustaw rozmiar czcionki na **18**.

5. Ustaw właściwość **TextAlign** na **MiddleCenter**.

6. Ustaw właściwość **Location** na **50, 75,** aby umieścić formant w formularzu.

7. Ustaw właściwość **(Name)** na **plusLeftLabel**.

8. Wybierz etykietę **plusLeftLabel** , a następnie wybierz klawisze **Ctrl** + **C** lub **Kopiuj** w menu **Edycja** .

9. Wklej etykietę trzy razy, wybierając klawisze **Ctrl** + **V** lub **Wklej** w menu **Edycja** .

10. Rozmieść trzy nowe etykiety tak, aby znajdowały się w wierszu z prawej strony etykiety **plusLeftLabel** .

     Możesz użyć linii rozdzielacza, aby rozprzestrzeniać je na zewnątrz i wyrównać je.

11. Ustaw wartość drugiej właściwości **Text** etykiety na **+** (znak plus).

12. Ustaw wartość trzeciej etykiety **(Name)** na **plusRightLabel**.

13. Ustaw wartość właściwości **tekst** czwartej etykiety na **=** (znak równości).

14. Dodaj <xref:System.Windows.Forms.NumericUpDown> formant z **przybornika**, ustaw jego rozmiar czcionki na **18** i ustaw jego szerokość na **100**.

     Dowiesz się więcej o tym rodzaju kontrolce później.

15. Wykreśl kontrolkę NumericUpDown z kontrolkami etykiet dla problemu dodawania.

16. Zmień wartość właściwości **(Name)** dla kontrolki NumericUpDown na **sum**.

     Utworzono pierwszy wiersz, jak pokazano na poniższej ilustracji.

     ![Pierwszy wiersz quizu matematycznego](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Aby dodać kontrolki do problemów odejmowania, mnożenia i dzielenia

1. Skopiuj wszystkie pięć formantów dla problemu dodawania (cztery kontrolki etykiet i formant NumericUpDown), a następnie wklej je.

     Formularz zawiera pięć nowych kontrolek, które są nadal zaznaczone.

2. Przenieś wszystkie kontrolki na miejsce, tak aby znajdowały się one poniżej formantów dodawania.

     Możesz użyć linii rozdzielacza, aby zapewnić wystarczającą odległość między dwoma wierszami.

3. Zmień wartość właściwości **Text** dla drugiej etykiety na **-** (znak minus).

4. Nadaj nazwę pierwszemu znakowi zapytania **minusLeftLabel**.

5. Nadaj drugiej nazwie etykietę **minusRightLabel**.

6. Nazwij **różnicę** kontrolki NumericUpDown.

7. Wklej pięć kontrolek dwa razy.

8. W trzecim wierszu nadaj pierwszej etykiecie **timesLeftLabel**, Zmień właściwość **tekst** drugiej etykiety na **×** (znak mnożenia), nazwij trzecią etykietę **timesRightLabel** i nazwij **produkt** Control NumericUpDown.

9. W czwartym wierszu nadaj pierwszej etykiecie **dividedLeftLabel**, Zmień właściwość **tekst** drugiej etykiety na **÷** (znak dzielenia), nadaj trzecią etykietę **dividedRightLabel** i nadaj jej nazwę **ilorazu**.

    > [!NOTE]
    > Możesz skopiować znak mnożenia × i ÷ znak dzielenia z tego samouczka i wkleić je do formularza.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Aby dodać przycisk Start i ustawić kolejność tabulacji

1. Dodaj <xref:System.Windows.Forms.Button> kontrolkę z **przybornika**, a następnie ustaw jej właściwość **(Name)** na **startButton**.

2. Ustaw właściwość **Text** , aby **uruchomić Quiz**.

3. Ustaw rozmiar czcionki na **14**.

4. Ustaw właściwość **AutoSize** na **true**, co spowoduje, że przycisk ma automatycznie zmieniać rozmiar w celu dopasowania do tekstu.

5. Wyśrodkuj przycisk w dolnej części formularza.

6. Ustaw wartość właściwości **TabIndex** dla formantu **startButton** na **1**.

    > [!NOTE]
    > Właściwość **TabIndex** ustawia kolejność formantów, gdy wybierany jest klawisz **Tab** . Aby zobaczyć, jak to działa, Otwórz dowolne okno dialogowe (na przykład na pasku menu wybierz **plik**  >  **Otwórz**), a następnie wybierz klawisz **Tab** kilka razy. Obejrzyj, jak kursor przemieszcza się z kontrolki, aby kontrolować każde wybranie klawisza **Tab** . Programista zdecydował o kolejności podczas tworzenia tego formularza.

7. Ustaw wartość właściwości **TabIndex** dla kontrolki sum NumericUpDown na **2**, dla kontrolki różnica na **3**, dla kontrolki produktu na **4**, a dla kontrolki ilorazu wartość **5**.

     Formularz powinien wyglądać podobnie do poniższego zrzutu ekranu.

     ![Początkowy formularz quizu matematycznego](../ide/media/express_formlaidout.png)

8. Aby sprawdzić, czy właściwość **TabIndex** działa zgodnie z oczekiwaniami, Zapisz i uruchom program, wybierając klawisz **F5** lub wybierając **Debuguj**  >  **Rozpocznij debugowanie** na pasku menu, a następnie wybierz klawisz **Tab** kilka razy.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 2. Tworzenie losowego problemu z dodaniem](../ide/step-2-create-a-random-addition-problem.md)**.

- Aby powrócić do tematu przeglądu, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).
