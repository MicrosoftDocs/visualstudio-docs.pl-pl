---
title: Krok 1. Tworzenie projektu i dodawanie etykiet do formularza
description: Dowiedz się, jak utworzyć projekt, dodać etykiety, przycisk i inne kontrolki do formularza oraz ustawić właściwości dla każdej kontrolki, która zostanie dodasz.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0400c29e53c45ad9a98e7edca78fd2cf9741fcf0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307755"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1. Tworzenie projektu i dodawanie etykiet do formularza

Pierwszym krokiem podczas opracowywania tego testu jest utworzenie projektu i dodanie etykiet, przycisku i innych kontrolek do formularza. Można również ustawić właściwości dla każdej kontrolki, która zostanie dodasz. Projekt będzie zawierać formularz, kontrolki i kod (w dalszej części samouczka). Przycisk uruchamia test, etykiety pokazują problemy z testem, a inne kontrolki pokazują odpowiedzi na test oraz czas, który pozostał do zakończenia testu.

> [!NOTE]
> Ten temat jest częścią serii samouczków dotyczących podstawowych pojęć związanych z kodowaniem. Aby uzyskać omówienie samouczka, zobacz [Samouczek 2: tworzenie testu matematycznego z timed .](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-create-a-project-for-a-form"></a>Aby utworzyć projekt dla formularza

::: moniker range="vs-2017"

1. Na pasku menu wybierz pozycję **Plik** > **Nowy** > **projekt.**

1. Wybierz pozycję **Visual C#** **lub Visual Basic** lewej  stronie okna dialogowego Nowy projekt, a następnie wybierz pozycję **Windows Desktop.**

1. Na liście szablonów wybierz szablon aplikacja Windows Forms **(.NET Framework),** nadaj jej nazwę *MathQuiz,* a następnie wybierz **przycisk OK.**

    Zostanie wyświetlony formularz o nazwie *Form1.cs* lub *Form1.vb* w zależności od wybranego języka programowania.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji Windows Forms (.NET Framework),** użyj szablonu Instalator programu Visual Studio, aby zainstalować obciążenie Tworzenie aplikacji klasycznych dla programu **.NET.**<br/><br/>![Obciążenie tworzenia aplikacji klasycznych dla programu .NET w Instalator programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz [stronę Visual Studio](../install/install-visual-studio.md) instalacji.

::: moniker-end

::: moniker range=">=vs-2019"

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Tworzenie nowego projektu** wprowadź lub wpisz *Windows Forms* w polu wyszukiwania. Następnie wybierz pozycję **Desktop** z **listy Typ** projektu.

   Po zastosowaniu **filtru Typ projektu** wybierz szablon **aplikacja Windows Forms (.NET Framework)** dla języka C# lub Visual Basic, a następnie wybierz pozycję **Dalej.**

   ![Wybierz szablon aplikacji Visual Basic C# lub Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli szablon aplikacji Windows Forms **(.NET Framework)** nie jest wyświetlony, możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj **więcej narzędzi i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie Wybierz tworzenie aplikacji **klasycznych dla programu .NET.**
   >
   > ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie.

1. W **oknie Configure your new project (Konfigurowanie** nowego projektu) wpisz lub wprowadź *MathQuiz* w **polu Project name (Nazwa** projektu). Następnie wybierz pozycję **Utwórz.**

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Aby ustawić właściwości formularza

1. W Visual Studio formularz *(Form1.cs* lub *Form1.vb*, w zależności od języka programowania), a następnie zmień jego właściwość **Text** na Test **matematycznych**.

     Okno **Właściwości** zawiera właściwości formularza.

1. Zmień rozmiar formularza na 500 pikseli szerokości na 400 pikseli wysokości.

     Rozmiar formularza można zmienić, przeciągając jego krawędzie, aż w lewym dolnym rogu zintegrowanego środowiska projektowego (IDE) pojawi się odpowiedni rozmiar. Alternatywnie możesz zmienić wartości właściwości **Size.**

1. Zmień wartość właściwości **FormBorderStyle** na **Fixed3D** i ustaw właściwość **MaximizeBox** na **false.**

     Te wartości uniemożliwiają uczestnikom testu zmienianie rozmiaru formularza.

## <a name="to-create-the-time-remaining-box"></a>Aby utworzyć pole czasu pozostałego do utworzenia

1. Dodaj <xref:System.Windows.Forms.Label> kontrolkę z **przybornika**, a następnie ustaw wartość jej właściwości **(Name)** na **timeLabel**.

     Ta etykieta stanie się polem w prawym górnym rogu, które pokazuje liczbę sekund, które pozostają w tece.

2. Zmień właściwość **AutoSize na** **False,** aby zmienić rozmiar pola.

3. Zmień właściwość **BorderStyle** na **FixedSingle,** aby narysować linię wokół pola.

4. Ustaw właściwość **Size** na **wartość 200, 30**.

5. Przenieś etykietę do prawego górnego rogu formularza, w którym będą wyświetlane niebieskie linie z kropką.

     Te wiersze ułatwiają wyrównywanie kontrolek w formularzu.

6. W **oknie** Właściwości wybierz właściwość **Text,** a następnie wybierz klawisz **Backspace,** aby wyczyścić jej wartość.

7. Wybierz znak plus ( ) obok właściwości Font, a następnie zmień wartość właściwości Size na **+** **15,75**.  

     Możesz zmienić kilka właściwości czcionki, jak pokazano na poniższym zrzucie ekranu.

     ![okno Właściwości przedstawiający rozmiar czcionki](../ide/media/express_setfontsize.png)

8. Dodaj kolejną kontrolkę Etykieta z **przybornika,** a następnie ustaw jej rozmiar czcionki **na 15,75**.

9. Ustaw właściwość **Text** na wartość **Time Left**.

10. Przenieś etykietę tak, aby była oznaczona lewą **etykietą timeLabel.**

### <a name="to-add-controls-for-the-addition-problems"></a>Aby dodać kontrolki dla problemów z dodawaniem

1. Dodaj kontrolkę Etykieta z **przybornika,** a następnie ustaw jej **właściwość Text** na **wartość ?** (znak zapytania).

2. Ustaw właściwość **AutoSize na** wartość **False.**

3. Ustaw właściwość **Size** na **wartość 60, 50**.

4. Ustaw rozmiar czcionki na **18**.

5. Ustaw właściwość **TextAlign na** **wartość MiddleCenter**.

6. Ustaw właściwość **Location** na **wartość 50, 75,** aby ustawić położenie kontrolki na formularzu.

7. Ustaw właściwość **(Name)** na **plusLeftLabel.**

8. Wybierz **etykietę plusLeftLabel,** a następnie wybierz klawisze **Ctrl** C lub +  **pozycję Kopiuj** w menu **Edycja.**

9. Wklej etykietę trzy razy, wybierając klawisze **Ctrl** V lub pozycję +  **Wklej** w menu **Edycja.**

10. Rozmieść trzy nowe etykiety tak, aby były w wierszu po prawej **stronie etykiety plusLeftLabel.**

     Możesz użyć linii cięgów, aby je przesłonić i wyproić w górę.

11. Ustaw wartość właściwości **Text** drugiej etykiety **+** na (znak plus).

12. Ustaw wartość właściwości **(Name)** trzeciej etykiety na **plusRightLabel**.

13. Ustaw wartość właściwości Text czwartej **etykiety** **=** na (znak równości).

14. Dodaj <xref:System.Windows.Forms.NumericUpDown> kontrolkę z **przybornika**, ustaw jej rozmiar czcionki na **18,** a szerokość na **100**.

     Więcej informacji na temat tego rodzaju kontroli dowiesz się później.

15. Aby rozwiązać problem z dodawaniem, dojmij kontrolkę NumericUpDown do kontrolek Etykieta.

16. Zmień wartość właściwości **(Name)** dla kontrolki NumericUpDown, aby zsumować wartość . 

     Pierwszy wiersz został utworzony, jak pokazano na poniższej ilustracji.

     ![Pierwszy wiersz testu matematycznego](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Aby dodać kontrolki dla problemów z odejmacją, mnożeniem i dzieleniem

1. Skopiuj wszystkie pięć kontrolek dla problemu z dodawaniem (cztery kontrolki Etykieta i Kontrolka NumericUpDown), a następnie wklej je.

     Formularz zawiera pięć nowych kontrolek, które są nadal zaznaczone.

2. Przenieś wszystkie kontrolki w miejsce tak, aby były w wierszu poniżej kontrolek dodatku.

     Możesz użyć linii siatki, aby zapewnić wystarczającą odległość między dwoma wierszami.

3. Zmień wartość właściwości **Text** drugiej etykiety na **-** (znak minus).

4. Nadaj pierwszej etykiecie znaku zapytania **nazwę minusLeftLabel.**

5. Nadaj drugiej etykiecie znaku zapytania **nazwę minusRightLabel**.

6. Nazwij kontrolkę NumericUpDown **.**

7. Wklej pięć kontrolek jeszcze dwa razy.

8. W trzecim wierszu nadaj pierwszej etykiecie nazwę **timesLeftLabel,** zmień właściwość **Text** drugiej etykiety na **×** (znak mnożenia), nadaj trzeciej etykiecie nazwę **timesRightLabel** i nazwij produkt sterujący NumericUpDown **.**

9. W czwartym wierszu nadaj pierwszej etykiecie nazwę **dividedLeftLabel,** zmień właściwość **Text** drugiej etykiety na **÷ (znak** dzielenia), nadaj trzeciej etykiecie nazwę **dividedRightLabel** i nadaj ilorazowi kontrolki NumericUpDown **.**

    > [!NOTE]
    > Możesz skopiować znak mnożenia × znak dzielenia ÷ z tego samouczka i wkleić je do formularza.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Aby dodać przycisk Start i ustawić kolejność tab-index

1. Dodaj <xref:System.Windows.Forms.Button> kontrolkę z **przybornika**, a następnie ustaw jej właściwość **(Name)** na **startButton**.

2. Ustaw właściwość **Text** na wartość **Rozpocznij test**.

3. Ustaw rozmiar czcionki na **14**.

4. Ustaw właściwość **AutoSize na** **wartość True,** co powoduje automatyczne zmienianie rozmiaru przycisku w celu dopasowania go do tekstu.

5. Wyśrodkuj przycisk w dolnej części formularza.

6. Ustaw wartość właściwości **TabIndex** kontrolki **startButton** na **1**.

    > [!NOTE]
    > Właściwość **TabIndex** określa kolejność kontrolek, gdy uczestnik testu wybierze klawisz **Tab.** Aby zobaczyć, jak to działa, otwórz dowolne okno dialogowe (na przykład na pasku menu wybierz pozycję Plik Otwórz), a następnie kilka  >  razy wybierz klawisz Tab.  Obserwuj sposób przesuwania kursora z kontrolki do kontrolki za każdym razem, gdy wybierasz **klawisz Tab.** Programista zdecydował o kolejności podczas tworzenia tego formularza.

7. Ustaw wartość właściwości **TabIndex** kontrolki Sum NumericUpDown na **2,** dla kontrolki różnicy na **3,** dla kontrolki produktu na **4,** a dla kontrolki ilorazu **wartość 5**.

     Formularz powinien wyglądać podobnie do poniższego zrzutu ekranu.

     ![Początkowy formularz testu matematycznego](../ide/media/express_formlaidout.png)

8. Aby sprawdzić, czy właściwość **TabIndex** działa zgodnie z oczekiwaniami, zapisz i uruchom program, wybierając klawisz **F5** lub wybierając pozycję **Debuguj** rozpocznij debugowanie na pasku menu, a następnie kilka razy wybierz klawisz  >   Tab. 

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 2. Tworzenie losowego problemu z dodawaniem](../ide/step-2-create-a-random-addition-problem.md)**.

- Aby wrócić do tematu z omówieniem, zobacz [Samouczek 2: tworzenie testu matematycznego z czasem.](../ide/tutorial-2-create-a-timed-math-quiz.md)
