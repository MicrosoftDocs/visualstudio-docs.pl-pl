---
title: Krok 1. Tworzenie projektu i Dodawanie etykiet do formularza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a13d96d8932a3a9e4628f2d0e67a28869252c95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667364"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1. Utworzenie projektu i dodawanie etykiet do formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pierwszym etapem tworzenia tego quizu jest utworzenie projektu i dodanie etykiet, przycisku i innych kontrolek do formularza. Należy również ustawić właściwości dla każdej dodawanej kontrolki. Projekt będzie zawierać formularz, formanty i (w dalszej części samouczka). Przycisk uruchamia quiz, etykiety pokazują problemy z quizem, a inne kontrolki wyświetlają odpowiedzi quizu i czas, który pozostanie do końca quizu.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby zapoznać się z omówieniem samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-create-a-project-and-set-properties-for-a-form"></a>Aby utworzyć projekt i ustawić właściwości formularza

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

2. Na liście **zainstalowane szablony** wybierz opcję **C#** lub **Visual Basic**.

3. Na liście szablonów wybierz szablon **aplikacji Windows Forms** , nadaj mu nazwę **Quiz matematyczny**, a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony formularz o nazwie **Form1.cs** lub **Form1. vb** , w zależności od wybranego języka programowania.

4. Wybierz formularz, a następnie zmień jego właściwość **Text** na **Quiz matematyczny**.

     Okno **Właściwości** zawiera właściwości dla formularza.

5. Zmień rozmiar formularza na 500 pikseli szerokości o 400 pikseli wysokości.

     Można zmienić rozmiar formularza, przeciągając jego krawędzie do momentu pojawienia się w lewym dolnym rogu zintegrowanego środowiska programistycznego (IDE). Alternatywnie można zmienić wartości właściwości **size** .

6. Zmień wartość właściwości **FormBorderStyle** na **Fixed3D**i ustaw właściwość **MaximizeBox** na **false**.

     Te wartości uniemożliwiają uczestnikomom quizu zmianę rozmiarów formularza.

### <a name="to-create-the-time-remaining-box"></a>Aby utworzyć pole pozostało czasu

1. Dodaj kontrolkę **etykieta** z przybornika, a następnie ustaw jej właściwość **(Name)** na wartość `timeLabel` .

     Ta etykieta zostanie umieszczony w prawym górnym rogu, która pokazuje liczbę sekund, które pozostaną w quizie.

2. Zmień właściwość **AutoSize** na **false** , aby można było zmienić rozmiar pola.

3. Zmień właściwość **BorderStyle** na **FixedSingle** , aby narysować linię wokół pola.

4. Ustaw właściwość **size** na **200, 30**.

5. Przenieś etykietę do prawego górnego rogu formularza, gdzie pojawią się niebieskie linie odstępu.

     Te wiersze ułatwiają wyrównywanie kontrolek w formularzu.

6. W oknie **Właściwości** wybierz właściwość **tekst** , a następnie wybierz klawisz Backspace, aby wyczyścić jego wartość.

7. Wybierz znak plus (+) obok właściwości **Font** , a następnie zmień wartość właściwości **size** na **15,75**.

     Można zmienić kilka właściwości czcionki, jak pokazano na poniższej ilustracji.

     ![Okno właściwości pokazywanie rozmiaru czcionki](../ide/media/express-setfontsize.png "Express_setFontSize") okno Właściwości pokazywanie rozmiaru czcionki

8. Dodaj kolejną kontrolkę **etykieta** z przybornika, a następnie ustaw jej rozmiar czcionki na **15,75**.

9. Ustaw właściwość **Text** na wartość **Time Left**.

10. Przenieś etykietę tak, aby była wierszem po lewej stronie etykiety **timeLabel** .

### <a name="to-add-controls-for-the-addition-problems"></a>Aby dodać kontrolki dla problemów dodatkowych

1. Dodaj kontrolkę **etykieta** z przybornika, a następnie ustaw jej właściwość **Text** na **?** (znak zapytania).

2. Ustaw właściwość **AutoSize** na **false**.

3. Ustaw właściwość **size** na **60, 50**.

4. Ustaw rozmiar czcionki na **18**.

5. Ustaw właściwość **TextAlign** na **MiddleCenter**.

6. Ustaw właściwość **Location** na **50, 75,** aby umieścić formant w formularzu.

7. Ustaw właściwość **(Name)** na **plusLeftLabel**.

8. Wybierz etykietę **plusLeftLabel** , a następnie wybierz klawisze CTRL + C lub **Kopiuj** w menu **Edycja** .

9. Wklej etykietę trzy razy, wybierając klawisze CTRL + V lub **Wklej** w menu **Edycja** .

10. Rozmieść trzy nowe etykiety tak, aby znajdowały się w wierszu z prawej strony etykiety **plusLeftLabel** .

     Możesz użyć linii rozdzielacza, aby rozprzestrzeniać je na zewnątrz i wyrównać je.

11. Ustaw wartość drugiej właściwości **Text** etykiety na **+** (znak plus).

12. Ustaw wartość trzeciej etykiety **(Name)** na **plusRightLabel**.

13. Ustaw wartość właściwości **tekst** czwartej etykiety na **=** (znak równości).

14. Dodaj formant **NumericUpDown** z przybornika, ustaw jego rozmiar czcionki na **18**i ustaw jego szerokość na **100**.

     Dowiesz się więcej o tym rodzaju kontrolce później.

15. Wykreśl kontrolkę **NumericUpDown** z kontrolkami etykiet dla problemu dodawania.

16. Zmień wartość właściwości **(Name)** dla kontrolki **NumericUpDown** na **sum**.

     Utworzono pierwszy wiersz, jak pokazano na poniższej ilustracji.

     ![Pierwszy wiersz quizu Matematycznego](../ide/media/express-firstrow.png "Express_firstRow") Pierwszy wiersz quizu matematycznego

### <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Aby dodać kontrolki do problemów odejmowania, mnożenia i dzielenia

1. Skopiuj wszystkie pięć formantów dla problemu dodawania (cztery kontrolki etykiet i formant NumericUpDown), a następnie wklej je.

     Formularz zawiera pięć nowych kontrolek, które są nadal zaznaczone.

2. Przenieś wszystkie kontrolki na miejsce, tak aby znajdowały się one poniżej formantów dodawania.

     Możesz użyć linii rozdzielacza, aby zapewnić wystarczającą odległość między dwoma wierszami.

3. Zmień wartość właściwości **Text** dla drugiej etykiety na **–** (znak minus).

4. Nadaj nazwę pierwszemu znakowi zapytania **minusLeftLabel**.

5. Nadaj drugiej nazwie etykietę **minusRightLabel**.

6. Nazwij **różnicę**kontrolki **NumericUpDown** .

7. Wklej pięć kontrolek dwa razy.

8. W trzecim wierszu nadaj pierwszej etykiecie **timesLeftLabel**, Zmień właściwość **tekst** drugiej etykiety na **×** (znak mnożenia), nazwij trzecią etykietę **timesRightLabel**i nazwij **produkt**Control NumericUpDown.

9. W czwartym wierszu nadaj pierwszej etykiecie **dividedLeftLabel**, Zmień właściwość **tekst** drugiej etykiety na **÷** (znak dzielenia), nadaj trzecią etykietę **dividedRightLabel**i nadaj jej nazwę **ilorazu**.

    > [!NOTE]
    > Możesz skopiować znak mnożenia × i ÷ znak dzielenia z tego samouczka i wkleić je do formularza.

### <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Aby dodać przycisk Start i ustawić kolejność tabulacji

1. Dodaj kontrolkę **Button** z przybornika, a następnie ustaw jej właściwość **(Name)** na **startButton**.

2. Ustaw właściwość **Text** , aby **uruchomić Quiz**.

3. Ustaw rozmiar czcionki na **14**.

4. Ustaw właściwość **AutoSize** na **true**, co spowoduje, że przycisk ma automatycznie zmieniać rozmiar w celu dopasowania do tekstu.

5. Wyśrodkuj przycisk w dolnej części formularza.

6. Ustaw wartość właściwości **TabIndex** dla formantu **startButton** na **1**.

    > [!NOTE]
    > Właściwość **TabIndex** ustawia kolejność formantów, gdy wybierany jest klawisz Tab. Aby zobaczyć, jak to działa, Otwórz dowolne okno dialogowe (na przykład na pasku menu wybierz **plik**, **Otwórz**), a następnie wybierz klawisz Tab kilka razy. Obejrzyj, jak kursor przemieszcza się z kontrolki, aby kontrolować każde wybranie klawisza Tab. Programista zdecydował o kolejności podczas tworzenia tego formularza.

7. Ustaw wartość właściwości **TabIndex** dla kontrolki sum NumericUpDown na **2**, dla kontrolki różnica na **3**, dla kontrolki produktu na **4**, a dla kontrolki ilorazu wartość **5**.

     Formularz powinien wyglądać jak na poniższej ilustracji.

     ![Początkowy formularz quizu Matematycznego](../ide/media/express-formlaidout.png "Express_FormLaidOut") Początkowy formularz quizu matematycznego

8. Aby sprawdzić, czy właściwość **TabIndex** działa zgodnie z oczekiwaniami, Zapisz i uruchom program, wybierając klawisz F5 lub wybierając **Debuguj**, **Rozpocznij debugowanie** na pasku menu, a następnie wybierz klawisz Tab kilka razy.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 2. Tworzenie losowego problemu z dodaniem](../ide/step-2-create-a-random-addition-problem.md).

- Aby powrócić do tematu przeglądu, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).
