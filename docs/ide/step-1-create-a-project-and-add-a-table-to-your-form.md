---
title: Krok 1. Tworzenie projektu i dodawanie tabeli do formularza
description: Dowiedz się, jak utworzyć projekt Matching Game i dodać tabelę do formularza.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed4c6b3c65cc7a4c68288c01964388bbf8ec54a0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306426"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1. Tworzenie projektu i dodawanie tabeli do formularza

Pierwszym krokiem w tworzeniu gry w dopasowanie jest stworzenie projektu i dodanie tabeli do formularza. Tabela ułatwia wyrównywanie ikon w uporządkowaną siatkę 4x4. Można również ustawić kilka właściwości, aby poprawić wygląd planszy gry.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Aby utworzyć projekt i dodać tabelę do formularza

::: moniker range="vs-2017"

1. Na pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

1. Wybierz pozycję **Visual C#** **lub Visual Basic** po lewej stronie okna dialogowego **Nowy** projekt, a następnie wybierz pozycję **Windows Desktop.**

1. Na liście szablonów wybierz szablon **Windows Forms App (.NET Framework),** nadaj jej nazwę *MatchingGame,* a następnie wybierz **przycisk OK.**

    Zostanie wyświetlony formularz o nazwie *Form1.cs* lub *Form1.vb,* w zależności od wybranego języka programowania.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Windows Forms App (.NET Framework),** użyj szablonu Instalator programu Visual Studio, aby zainstalować obciążenie tworzenie aplikacji klasycznych dla programu **.NET.**<br/><br/>![Obciążenie tworzenia aplikacji klasycznych dla programu .NET w Instalator programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz [stronę Visual Studio](../install/install-visual-studio.md) instalacji.

::: moniker-end

::: moniker range=">=vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Tworzenie nowego projektu** wprowadź lub wpisz *Windows Forms* w polu wyszukiwania. Następnie wybierz pozycję **Desktop** z **listy Typ** projektu.

   Po zastosowaniu **filtru Project type** (Typ projektu) wybierz **szablon Windows Forms App (.NET Framework)** dla języka C# lub Visual Basic, a następnie wybierz pozycję **Next (Dalej).**

   ![Wybierz szablon aplikacji Visual Basic C# lub Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli szablon aplikacji Windows Forms **(.NET Framework)** nie jest wyświetlony, możesz go zainstalować w **oknie Tworzenie nowego** projektu. W **komunikacie Nie można znaleźć tego,** czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie Wybierz tworzenie aplikacji **klasycznych dla programu .NET.**
   >
   > ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie.

1. W **oknie Konfigurowanie nowego projektu** wpisz lub wprowadź *matchinggame* w **polu Nazwa** projektu. Następnie wybierz pozycję **Utwórz**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Aby ustawić właściwości formularza

1. W **oknie** Właściwości ustaw następujące właściwości formularza.

   1. Zmień właściwość Text formularza **z Form1** na **Matching Game**.  Ten tekst jest wyświetlany w górnej części okna gry.

   2. Ustaw rozmiar formularza na 550 pikseli szerokości i 550 pikseli wysokości. Można to zrobić, ustawiając właściwość **Size** na **550, 550** lub przeciągając róg formularza, aż w prawym dolnym rogu zintegrowanego środowiska projektowego (IDE) zostanie wyświetlony prawidłowy rozmiar.

2. Wyświetl przybornik, wybierając kartę **Przybornik** po lewej stronie środowiska IDE.

3. Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę z **kategorii Kontenery** w przyborniku, a następnie ustaw dla niego następujące właściwości.

   1. Ustaw właściwość **BackColor** na **Wartość CornflowerBlue.** W tym celu otwórz **okno dialogowe BackColor,** wybierając strzałkę listy rozwijanej obok właściwości **BackColor** w **oknie** Właściwości.  Następnie wybierz kartę **Sieć Web** w oknie **dialogowym BackColor,** aby wyświetlić listę dostępnych nazw kolorów.

      > [!NOTE]
      > Kolory nie są w kolejności alfabetycznej, a **CornflowerBlue** znajduje się w dolnej części listy.

   2. Ustaw właściwość **Dock** na **Fill,** wybierając przycisk listy rozwijanej obok właściwości i wybierając duży środkowy przycisk. Tabela się rozszerza i obejmuje cały formularz.

   3. Ustaw właściwość **CellBorderStyle** na **wartość Inset**. Zapewnia to wizualne granice pomiędzy poszczególnymi komórkami na planszy.

   4. Kliknij przycisk trójkąta w prawym górnym rogu formantu TableLayoutPanel, aby wyświetlić jego menu zadań.

   5. W menu zadań  wybierz dwukrotnie pozycję Dodaj wiersz, aby dodać jeszcze dwa wiersze, a następnie wybierz pozycję Dodaj kolumnę **dwa** razy, aby dodać jeszcze dwie kolumny.

   6. W menu zadań wybierz pozycję Edytuj **wiersze i kolumny,** aby otworzyć **okno Style kolumn i** wierszy. Wybierz każdą z kolumn, wybierz przycisk **opcji Procent,** a następnie ustaw szerokość każdej kolumny na 25 procent całkowitej szerokości. Następnie wybierz **pozycję Wiersze** w polu listy rozwijanej w górnej części okna i ustaw wysokość każdego wiersza na 25 procent. Gdy wszystko będzie gotowe, wybierz przycisk **OK.**

      TableLayoutPanel powinien być teraz siatką 4 x 4, o szesnastu kwadratowych komórkach równej wielkości. Te wiersze i kolumny są tam, gdzie później pojawią się obrazy ikon.

4. Należy się upewnić, że TableLayoutPanel jest zaznaczony w edytorze formularza. Aby to sprawdzić, w górnej części okna **Właściwości** powinien zostać wyświetlony **tableLayoutPanel1.** Jeśli nie jest zaznaczone, wybierz tableLayoutPanel w formularzu lub wybierz go w kontrolce listy rozwijanej w górnej **części okna** Właściwości.

    Po wybraniu kontrolki TableLayoutPanel otwórz przybornik i dodaj kontrolkę (znajdującą się w kategorii Formanty wspólne) do lewej górnej komórki kontrolki <xref:System.Windows.Forms.Label> TableLayoutPanel.  Kontrolka etykiety powinna być teraz zaznaczona w idee . Ustaw dla niego następujące właściwości.

   1. Upewnij się, że właściwość **BackColor etykiety** jest ustawiona na **CornflowerBlue.**

   2. Ustaw właściwość **AutoSize na** **wartość False**.

   3. Ustaw właściwość **Dock** na **fill**.

   4. Ustaw właściwość **TextAlign na** **wartość MiddleCenter,** wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając środkowy przycisk. Gwarantuje to, że ikona pojawia się w środku komórki.

   5. Wybierz właściwość **Font.** Powinien zostać wyświetlony przycisk wielokropka (**...**).

   6. Wybierz przycisk wielokropka,  a następnie ustaw wartość czcionki  na **Webdings,** styl czcionki na Bold **i** **rozmiar** **na 48**.

   7. Ustaw właściwość **Text** etykiety na literę **c**.

        Lewa górna komórka w TableLayoutPanel powinna teraz zawierać czarne pole wyśrodkowane na niebieskim tle.

       > [!NOTE]
       > Czcionka Webdings to czcionka ikon, która jest dostarczana z systemem operacyjnym Windows. W grze w dopasowywanie, gracz musi dopasować pary ikon, więc ta czcionka jest używana do wyświetlania dopasowywanych ikon. Zamiast umieszczać **wartość c** we właściwości **Text,** spróbuj wprowadzić różne litery, aby zobaczyć, jakie ikony są wyświetlane. Znak wykrzyknika to pająk, wielkie N to oko, a przecinek to papryczka chili.

5. Wybierz kontrolkę Etykieta i skopiuj ją do następnej komórki w tableLayoutPanel. (Wybierz **klawisz Ctrl** + **Klucze** języka C lub na pasku menu wybierz pozycję **Edytuj**  >  **kopię).** Następnie wklej go. (Wybierz **klawisz Ctrl** + **Klawisze** V lub na pasku menu wybierz pozycję **Edytuj**  >  **wklejanie).** Kopia pierwszej etykiety zostanie wyświetlona w drugiej komórce tableLayoutPanel. Wklej ją ponownie, a w trzeciej komórce pojawi się inna etykieta. Wklejaj kontrolki Etykieta do momentu wypełnienia wszystkich komórek.

   > [!NOTE]
   > Jeśli wklejasz zbyt wiele razy, ide dodaje nowy wiersz do tableLayoutPanel, dzięki czemu ma miejsce na dodanie nowej kontrolki Etykieta. Można cofnąć tę operację. Aby usunąć nową komórkę, wybierz klawisze **Ctrl** Z lub na +  pasku menu wybierz pozycję **Edytuj**  >  **cofnij.**

    Teraz formularz jest rozeplanowyny. Powinna ona wyglądać podobnie do poniższej ilustracji.

    ![Początkowy formularz gry w dopasowywanie](../ide/media/express_tut4step1.png)<br/>*Początkowy formularz gry w dopasowywanie*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [Krok 2. Dodawanie obiektu Random i lista ikon.](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)

- Aby wrócić do tematu z omówieniem, zobacz [Samouczek 3: tworzenie gry w dopasowywanie.](../ide/tutorial-3-create-a-matching-game.md)
