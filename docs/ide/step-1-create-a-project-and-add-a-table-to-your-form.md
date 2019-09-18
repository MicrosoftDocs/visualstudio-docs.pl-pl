---
title: Krok 1. Tworzenie projektu i dodawanie tabeli do formularza
ms.date: 05/31/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e7d11f023cc239a3aaa4124cb1ac12a4e4ae9eb
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079609"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1. Tworzenie projektu i dodawanie tabeli do formularza

Pierwszym krokiem w tworzeniu gry w dopasowanie jest stworzenie projektu i dodanie tabeli do formularza. Tabela ułatwia wyrównywanie ikon w uporządkowaną siatkę 4x4. Można również ustawić kilka właściwości, aby poprawić wygląd planszy gry.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Aby utworzyć projekt i dodać tabelę do formularza

::: moniker range="vs-2017"

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. Wybierz pozycję  **C# Wizualizacja** lub **Visual Basic** po lewej stronie okna dialogowego **Nowy projekt** , a następnie wybierz pozycję **Windows Desktop**.

1. Na liście szablonów wybierz szablon **aplikacja Windows Forms (.NET Framework)** , nadaj mu nazwę *MatchingGame*, a następnie wybierz przycisk **OK** .

    Zostanie wyświetlony formularz o nazwie *Form1.cs* lub *Form1. vb* , w zależności od wybranego języka programowania.

   > [!NOTE]
   > Jeśli szablon **aplikacji Windows Forms (.NET Framework)** nie jest widoczny, użyj Instalator programu Visual Studio, aby zainstalować obciążenie **programistyczne dla programu .NET Desktop** .<br/><br/>![Obciążenie Programowanie aplikacji klasycznych platformy .NET w Instalator programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz stronę [Instalowanie programu Visual Studio](../install/install-visual-studio.md) .

::: moniker-end

::: moniker range="vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wprowadź lub wpisz *Windows Forms* w polu wyszukiwania.

1. Wybierz szablon **aplikacja Windows Forms (.NET Framework)** , a następnie wybierz przycisk **dalej**.

   ![Wybierz szablon Visual Basic dla aplikacji Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli szablon **aplikacji Windows Forms (.NET Framework)** nie jest wyświetlany, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** .
   >
   > ![Obciążenie platformy .NET core w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie.

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MatchingGame* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Aby ustawić właściwości formularza

1. W oknie **Właściwości** ustaw następujące właściwości formularza.

   1. Zmień właściwość **Text** formularza z **Form1** na **pasującą grę**. Ten tekst jest wyświetlany w górnej części okna gry.

   2. Ustaw rozmiar formularza na 550 pikseli szerokości i 550 pikseli wysokości. Można to zrobić, ustawiając właściwość **size** na **550, 550**lub przeciągając róg formularza do momentu, gdy zobaczysz właściwy rozmiar w prawym dolnym rogu zintegrowanego środowiska programistycznego (IDE).

2. Wyświetl Przybornik, wybierając kartę **Przybornik** po lewej stronie IDE.

3. Przeciągnij formant z kategorii kontenery w przyborniku, a następnie ustaw dla niego następujące właściwości. <xref:System.Windows.Forms.TableLayoutPanel>

   1. Ustaw właściwość **BackColor** na **CornflowerBlue**. Aby to zrobić, Otwórz okno dialogowe **BackColor** , wybierając strzałkę listy rozwijanej obok właściwości **BackColor** w oknie **Właściwości** .  Następnie wybierz kartę **Sieć Web** w oknie dialogowym **BackColor** , aby wyświetlić listę dostępnych nazw kolorów.

      > [!NOTE]
      > Kolory nie są w kolejności alfabetycznej, a **CornflowerBlue** znajduje się w dolnej części listy.

   2. Ustaw właściwość **Dock** na wartość **Fill** , wybierając przycisk listy rozwijanej obok właściwości i wybierając przycisk z dużymi środkami. Tabela się rozszerza i obejmuje cały formularz.

   3. Ustaw właściwość **CellBorderStyle** na wartość **Wstaw**. Zapewnia to wizualne granice pomiędzy poszczególnymi komórkami na planszy.

   4. Kliknij przycisk trójkąta w prawym górnym rogu formantu TableLayoutPanel, aby wyświetlić jego menu zadań.

   5. W menu zadania wybierz dwa razy **Dodaj wiersz** , aby dodać dwa wiersze, a następnie wybierz dwa razy **Dodaj kolumnę** , aby dodać dwie kolumny.

   6. W menu zadania wybierz polecenie **Edytuj wiersze i kolumny** , aby otworzyć okno **Style kolumn i wierszy** . Wybierz każdą z kolumn, wybierz przycisk opcji **procent** , a następnie ustaw szerokość każdej kolumny na 25 procent całkowitej szerokości. Następnie wybierz pozycję **wiersze** w polu listy rozwijanej w górnej części okna, a następnie ustaw wysokość każdego wiersza na 25 procent. Gdy wszystko będzie gotowe, wybierz przycisk **OK** .

      TableLayoutPanel powinien być teraz siatką 4 x 4, o szesnastu kwadratowych komórkach równej wielkości. Te wiersze i kolumny są tam, gdzie później pojawią się obrazy ikon.

4. Należy się upewnić, że TableLayoutPanel jest zaznaczony w edytorze formularza. Aby to sprawdzić, należy zobaczyć **tableLayoutPanel1** w górnej części okna **Właściwości** . Jeśli nie jest zaznaczone, wybierz TableLayoutPanel w formularzu lub wybierz go w kontrolce menu rozwijanego u góry okna **Właściwości** .

    Gdy TableLayoutPanel jest zaznaczone, Otwórz przybornik i Dodaj <xref:System.Windows.Forms.Label> kontrolkę (znajdującą się w kategorii **Formanty standardowe** ) do lewej górnej komórki TableLayoutPanel. Kontrolka etykieta powinna być teraz zaznaczona w IDE. Ustaw dla niego następujące właściwości.

   1. Upewnij się, że właściwość " **BackColor** " etykiety jest ustawiona na **CornflowerBlue**.

   2. Ustaw właściwość **AutoSize** na **false**.

   3. Ustaw właściwość **Dock** na **Fill**.

   4. Ustaw właściwość **TextAlign** na **MiddleCenter** , wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając środkowy przycisk. Gwarantuje to, że ikona pojawia się w środku komórki.

   5. Wybierz właściwość **Font** . Powinien pojawić się przycisk wielokropka ( **...** ).

   6. Wybierz przycisk wielokropka, a następnie ustaw wartość **czcionki** na **Webdings**, **styl czcionki** na **pogrubiony**, a **rozmiar** na **48**.

   7. Ustaw właściwość **Text** etykiety na literę **c**.

        Lewa górna komórka w TableLayoutPanel powinna teraz zawierać czarne pole wyśrodkowane na niebieskim tle.

       > [!NOTE]
       > Czcionka Webdings to czcionka ikon, która jest dostarczana z systemem operacyjnym Windows. W grze w dopasowywanie, gracz musi dopasować pary ikon, więc ta czcionka jest używana do wyświetlania dopasowywanych ikon. Zamiast umieszczać **c** we właściwości **Text** , spróbuj wprowadzić różne litery, aby zobaczyć, jakie ikony są wyświetlane. Znak wykrzyknika to pająk, wielkie N to oko, a przecinek to papryczka chili.

5. Wybierz kontrolkę etykieta i skopiuj ją do następnej komórki w TableLayoutPanel. (Wybierz klawisze **Ctrl**+**C** lub na pasku menu, wybierz polecenie **Edytuj** > **kopię**). Następnie wklej go. (Wybierz klawisze **Ctrl**+**V** lub na pasku menu wybierz polecenie **Edytuj** > **Wklej**). Kopia pierwszej etykiety pojawia się w drugiej komórce TableLayoutPanel. Wklej ją ponownie, a w trzeciej komórce pojawi się inna etykieta. Kontynuuj wklejanie kontrolek etykiet do momentu wypełnienia wszystkich komórek.

   > [!NOTE]
   > Jeśli wkleisz zbyt wiele razy, IDE dodaje nowy wiersz do TableLayoutPanel, tak aby miał miejsce dodać nową kontrolkę etykieta. Można cofnąć tę operację. Aby usunąć nową komórkę,**wybierz klawisze** **Ctrl +** +lub na pasku menu wybierz polecenie **Edytuj** > **Cofnij**.

    Teraz formularz jest rozmieszczony. Powinien wyglądać podobnie do poniższej ilustracji.

    ![Początkowy pasujący formularz gry](../ide/media/express_tut4step1.png)<br/>*Początkowy pasujący formularz gry*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 2: Dodaj losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Aby powrócić do tematu przeglądu, zobacz [samouczek 3: Utwórz pasującą grę](../ide/tutorial-3-create-a-matching-game.md).
