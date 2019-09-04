---
title: Krok 1. Tworzenie projektu aplikacji Windows Forms
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc2b21edcae4cd825ade551b92f98853da8f2516
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293664"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Krok 1. Tworzenie projektu aplikacji Windows Forms

Podczas tworzenia przeglądarki obrazów pierwszym krokiem jest utworzenie projektu aplikacji Windows Forms.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Open Visual Studio 2017

1. Na pasku menu wybierz **pliku** > **New** > **projektu**. Okno dialogowe powinno wyglądać podobnie do poniższego zrzutu ekranu.

     ![Okno dialogowe Nowy projekt](../ide/media/newprojectdialogcallouts.png)<br/>***Nowy projekt*** okno *dialogowe*

2. Po lewej stronie okna dialogowego **Nowy projekt** wybierz pozycję **Wizualizacja C#**  lub **Visual Basic**, a następnie wybierz pozycję **Windows Desktop**.

3. Na liście szablony projektu wybierz pozycję **aplikacja Windows Forms (.NET Framework)** . Nazwij nowy formularz *PictureViewer*, a następnie wybierz przycisk **OK** .

    >[!NOTE]
    >Jeśli szablon **aplikacji Windows Forms (.NET Framework)** nie jest widoczny, użyj Instalator programu Visual Studio, aby zainstalować obciążenie **programistyczne dla programu .NET Desktop** .<br/><br/>![Obciążenie Programowanie aplikacji klasycznych platformy .NET w Instalator programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz stronę [Instalowanie programu Visual Studio](../install/install-visual-studio.md) .

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Open Visual Studio 2019

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wprowadź lub wpisz *Windows Forms* w polu wyszukiwania. Następnie wybierz pozycję **pulpit** z listy **Typ projektu** .

   Po zastosowaniu filtru **Typ projektu** wybierz szablon **aplikacja Windows Forms (.NET Framework)** dla obu C# lub Visual Basic, a następnie wybierz przycisk **dalej**.

   ![Wybierz C# szablon aplikacji Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli szablon **aplikacji Windows Forms (.NET Framework)** nie jest widoczny, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** .
   >
   > ![Obciążenie platformy .NET core w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie.

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *PictureViewer* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

::: moniker-end

Program Visual Studio tworzy rozwiązanie dla Twojego programu. Rozwiązanie pełni rolę kontenera dla wszystkich projektów i plików wymaganych przez program. Te warunki zostaną omówione bardziej szczegółowo w dalszej części tego samouczka.

## <a name="about-the-windows-forms-application-project"></a>Informacje o projekcie aplikacji Windows Forms

1. Środowisko deweloperskie zawiera trzy okna: okno główne, **Eksplorator rozwiązań**i okno **Właściwości** .

     Jeśli brakuje któregoś z tych okienek, możesz przywrócić domyślny układ okna. Na pasku menu wybierz kolejno **okna** > **Resetuj układ okna**.

     Możesz również wyświetlić okna przy użyciu poleceń menu. Na pasku menu wybierz **Widok** > **Właściwości okno** lub **Eksplorator rozwiązań**.

     Jeśli jakiekolwiek inne okna są otwarte, zamknij je, wybierając przycisk **Zamknij** (x) w prawym górnym rogu.

    ::: moniker range="vs-2017"

    * **Okno główne** W tym oknie można wykonywać większość prac, takich jak praca z formularzami i edytowanie kodu. Okno wyświetla formularz w **Edytorze formularzy**. W górnej części okna zostanie wyświetlona karta **Strona początkowa** i karta **Form1.cs [Design]** . (W Visual Basic Nazwa karty zostanie zakończona z *. vb* zamiast *. cs*).

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Okno główne** W tym oknie można wykonywać większość prac, takich jak praca z formularzami i edytowanie kodu. Okno wyświetla formularz w **Edytorze formularzy**.

    ::: moniker-end

    * **Okno Eksplorator rozwiązań** W tym oknie można wyświetlać wszystkie elementy w rozwiązaniu i przechodzić do nich.

       W przypadku wybrania pliku zawartość okna **Właściwości** zostanie zmieniona. Jeśli otworzysz plik kodu (który zostanie zakończony w *. cs* w C# i *. vb* w Visual Basic), zostanie wyświetlony plik kodu lub Projektant pliku kodu. Projektant jest powierzchnią wizualną, na której można dodawać kontrolki, takie jak przyciski i listy. W przypadku formularzy programu Visual Studio Projektant jest nazywany **Projektant formularzy systemu Windows**.

    * **Okno właściwości** W tym oknie można zmienić właściwości elementów wybranych w innych oknach. Na przykład po wybraniu formularza Form1 można zmienić jego tytuł przez ustawienie właściwości **Text** i zmienić kolor tła, ustawiając właściwość **BackColor** .

      > [!NOTE]
      > W górnym wierszu **Eksplorator rozwiązań** przedstawiono **rozwiązanie "PictureViewer" (1 projekt)** , co oznacza, że program Visual Studio utworzył rozwiązanie. Rozwiązanie może zawierać więcej niż jeden projekt, ale teraz będzie można korzystać z rozwiązań, które zawierają tylko jeden projekt.

1. Na pasku menu wybierz kolejno opcje **plik** > **Zapisz wszystko**.

     Alternatywnie wybierz na pasku narzędzi przycisk **Zapisz wszystko** , który zostanie wyświetlony na poniższym obrazie.

     ![Przycisk Zapisz wszystkie paski narzędzi](../ide/media/express_iconsaveall.png)<br/>
     ***Zapisz wszystko*** *przycisk paska narzędzi*

     Program Visual Studio automatycznie wypełnia nazwę folderu i nazwę projektu, a następnie zapisuje projekt w folderze projektów.

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz [krok 2: Uruchom program](../ide/step-2-run-your-program.md).

* Aby powrócić do tematu przeglądu, zobacz [samouczek 1: Utwórz przeglądarkę](../ide/tutorial-1-create-a-picture-viewer.md)obrazów.

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie quizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry zgodnej](tutorial-3-create-a-matching-game.md)
