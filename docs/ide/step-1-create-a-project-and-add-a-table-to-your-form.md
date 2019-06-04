---
title: Krok 1. Tworzenie projektu i Dodawanie tabeli do formularza
ms.date: 05/31/2019
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64ebd8469eb763af9565609dd680ba1e256ed6c5
ms.sourcegitcommit: aeb1a1135dd789551e15aa5124099a5fe3f0f32b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66501155"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1. Tworzenie projektu i Dodawanie tabeli do formularza

Pierwszym krokiem w tworzeniu gry w dopasowanie jest stworzenie projektu i dodanie tabeli do formularza. Tabela ułatwia wyrównywanie ikon w uporządkowaną siatkę 4x4. Można również ustawić kilka właściwości, aby poprawić wygląd planszy gry.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Aby utworzyć projekt i dodać tabelę do formularza

::: moniker range="vs-2017"

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

1. Wybierz **Visual C#**  lub **języka Visual Basic** w lewej części **nowy projekt** okna dialogowego pole, a następnie wybierz **Windows Desktop**.

1. Z listy szablonów wybierz **aplikacji programu Windows Forms (.NET Framework)** szablonu, nadaj jej nazwę *nazwę MatchingGame*, a następnie wybierz **OK** przycisku.

    Formularz, który nosi nazwę *Form1.cs* lub *Form1.vb* pojawia się w zależności od języka programowania, który został wybrany.

   > [!NOTE]
   > Jeśli nie widzisz **aplikacji programu Windows Forms (.NET Framework)** szablon, użyj Instalatora programu Visual Studio, aby zainstalować **programowanie aplikacji klasycznych dla platformy .NET** obciążenia.<br/><br/>![Obciążenie programowanie aplikacji klasycznych dla platformy .NET w Instalatorze programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz [Zainstaluj program Visual Studio](../install/install-visual-studio.md) strony.

::: moniker-end

::: moniker range="vs-2019"

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

   ![Wyświetlanie w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na **Utwórz nowy projekt** oknie wprowadź lub wpisz *Windows Forms* w polu wyszukiwania.

1. Wybierz **aplikacji programu Windows Forms (.NET Framework)** szablonu, a następnie wybierz **dalej**.

   ![Wybierz szablon języka Visual Basic w aplikacji Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz **aplikacji programu Windows Forms (.NET Framework)** szablonu, można zainstalować go z **Utwórz nowy projekt** okna. W **nie znaleźć, czego szukasz?** komunikatu, wybierz polecenie **zainstalować więcej narzędzi i funkcji** łącza.
   >
   > ![Łącza "Zainstaluj więcej narzędzi i funkcji" komunikat "Nie możesz znaleźć teraz wyszukiwanie" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalatorze programu Visual Studio, wybierz pozycję Wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążenia.
   >
   > ![Obciążenie platformy .NET core w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie należy wybrać **Modyfikuj** przycisku w Instalatorze programu Visual Studio. Może zostać wyświetlony monit, aby zapisać swoją pracę; Jeśli tak, należy to zrobić. Następnie wybierz pozycję **Kontynuuj** do zainstalowania z obciążeniem.

1. W **konfigurowania nowego projektu** oknie wpisz lub wprowadź *nazwę MatchingGame* w **Nazwa projektu** pole. Następnie wybierz **Utwórz**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Aby ustawić właściwości dla formularza

1. W **właściwości** okna, ustaw następujące właściwości formularza.

   1. Formularz zmiany **tekstu** właściwość **Form1** do **gra w dopasowywanie**. Ten tekst jest wyświetlany w górnej części okna gry.

   2. Ustaw rozmiar formularza na 550 pikseli szerokości i 550 pikseli wysokości. Możesz to zrobić, ustawiając **rozmiar** właściwości **550, 550**, lub poprzez przeciąganie rogu formularza, aż zobaczysz właściwy rozmiar w prawym dolnym rogu zintegrowanego rozwoju (środowiska ŚRODOWISKO IDE).

2. Wyświetl przybornik, wybierając **przybornika** karty po lewej stronie IDE.

3. Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **kontenery** kategorii w przyborniku, a następnie ustaw następujące właściwości dla niego.

   1. Ustaw **BackColor** właściwości **CornflowerBlue**. Aby to zrobić, otwórz **BackColor** okno dialogowe, wybierając strzałkę listy rozwijanej obok **BackColor** właściwość **właściwości** okna.  Następnie wybierz **Web** karcie **BackColor** okno dialogowe, aby wyświetlić listę nazw dostępnych kolorów.

      > [!NOTE]
      > Kolory nie są w kolejności alfabetycznej, a **CornflowerBlue** znajduje się w pobliżu dolnej części listy.

   2. Ustaw **Dock** właściwości **wypełnienia** wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając duży środkowy przycisk. Tabela się rozszerza i obejmuje cały formularz.

   3. Ustaw **CellBorderStyle** właściwości **Inset**. Zapewnia to wizualne granice pomiędzy poszczególnymi komórkami na planszy.

   4. Kliknij przycisk trójkąta w prawym górnym rogu formantu TableLayoutPanel, aby wyświetlić jego menu zadań.

   5. W menu zadań wybierz **Dodaj wiersz** dwa razy, aby dodać dwa wiersze, a następnie wybierz **Dodaj kolumnę** dwa razy, aby dodać dwie kolumny.

   6. W menu zadań wybierz **Edytuj wiersze i kolumny** otworzyć **Style kolumn i wierszy** okna. Wybierz każdą z kolumn, wybierz pozycję **procent** przycisk opcji, a następnie ustaw szerokość każdej kolumny na 25 procent ogólnej szerokości. Następnie wybierz pozycję **wierszy** z listy rozwijanej w górnej części okna i Ustaw wysokość każdego wiersza na 25 procent. Gdy wszystko będzie gotowe, wybierz pozycję **OK** przycisku.

      TableLayoutPanel powinien być teraz siatką 4 x 4, o szesnastu kwadratowych komórkach równej wielkości. Te wiersze i kolumny są tam, gdzie później pojawią się obrazy ikon.

4. Należy się upewnić, że TableLayoutPanel jest zaznaczony w edytorze formularza. Aby to sprawdzić, powinien zostać wyświetlony **tableLayoutPanel1** w górnej części **właściwości** okna. Jeśli nie jest zaznaczone, wybierz TableLayoutPanel na formularzu lub wybierz go z rozwijanej listy formantów u góry **właściwości** okna.

    Gdy TableLayoutPanel jest zaznaczony, Otwórz przybornik i Dodaj <xref:System.Windows.Forms.Label> kontroli (znajdujący się w **wspólnych formantów** kategoria) do lewej górnej komórki TableLayoutPanel. Formant etykiety powinny teraz być zaznaczone w środowisku IDE. Ustaw dla niego następujące właściwości.

   1. Upewnij się, że etykiety **BackColor** właściwość jest ustawiona na **CornflowerBlue**.

   2. Ustaw **AutoSize** właściwości **False**.

   3. Ustaw **Dock** właściwości **wypełnienia**.

   4. Ustaw **TextAlign** właściwości **MiddleCenter** , wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając środkowy przycisk. Gwarantuje to, że ikona pojawia się w środku komórki.

   5. Wybierz **czcionki** właściwości. Wielokropek ( **...** ) powinien pojawić się przycisk.

   6. Wybierz przycisk wielokropka i ustaw **czcionki** wartość **Webdings**, **styl czcionki** do **Bold**i **rozmiar** do **48**.

   7. Ustaw **tekstu** właściwość etykiety na literę **c**.

        Lewa górna komórka w TableLayoutPanel powinna teraz zawierać czarne pole wyśrodkowane na niebieskim tle.

       > [!NOTE]
       > Czcionka Webdings to czcionka ikon, która jest dostarczana z systemem operacyjnym Windows. W grze w dopasowywanie, gracz musi dopasować pary ikon, więc ta czcionka jest używana do wyświetlania dopasowywanych ikon. Zamiast umieszczać **c** w **tekstu** właściwość, spróbuj wprowadzić różne litery, aby zobaczyć, jakie ikony są wyświetlane. Znak wykrzyknika to pająk, wielkie N to oko, a przecinek to papryczka chili.

5. Wybierz formant etykiety i skopiuj go do następnej komórki w TableLayoutPanel. (Wybierz **Ctrl**+**C** kluczy lub na pasku menu wybierz **Edytuj** > **kopiowania**.) Następnie wklej go. (Wybierz **Ctrl**+**V** kluczy lub na pasku menu wybierz **Edytuj** > **Wklej**.) W drugiej komórce TableLayoutPanel pojawi się kopia pierwszej etykiety. Wklej ją ponownie, a inny etykieta jest wyświetlana w trzeciej komórce. Wklejaj formanty etykiet, aż wszystkie komórki zostaną wypełnione.

   > [!NOTE]
   > Jeśli wkleisz zbyt wiele razy, IDE doda nowy wiersz do TableLayoutPanel, tak, aby miało miejsce na dodanie nowego formantu etykiety. Można cofnąć tę operację. Aby usunąć nową komórkę, wybierz **Ctrl**+**Z** kluczy lub na pasku menu wybierz **Edytuj** > **Cofnij**.

    Teraz formularz jest rozmieszczony. Powinien wyglądać tak, jak na poniższej ilustracji:

    ![Początkowy formularz gry w dopasowywanie](../ide/media/express_tut4step1.png)<br/>   Początkowy formularz gry w dopasowywanie

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 2: Dodawanie obiektu Random i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Aby powrócić do tematu przeglądu, zobacz [Tutorial 3: Utwórz pasujący obiekt typu gier](../ide/tutorial-3-create-a-matching-game.md).
