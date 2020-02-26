---
title: Krok 1. Tworzenie projektu aplikacji Windows Forms
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5e34d825d2a4d296a8a394105b412195b4e3fb
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579913"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Krok 1. Tworzenie projektu aplikacji Windows Forms

Podczas tworzenia przeglądarki obrazów pierwszym krokiem jest utworzenie projektu aplikacji Windows Forms.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Open Visual Studio 2017

1. Na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**. Okno dialogowe powinno wyglądać podobnie do poniższego zrzutu ekranu.

     okno dialogowe ![nowego projektu](../ide/media/newprojectdialogcallouts.png)<br/>***Nowy projekt*** — okno *dialogowe*

2. Po lewej stronie okna dialogowego **Nowy projekt** wybierz pozycję **Wizualizacja C#**  lub **Visual Basic**, a następnie wybierz pozycję **Windows Desktop**.

3. Na liście szablony projektu wybierz pozycję **aplikacja Windows Forms (.NET Framework)** . Nazwij nowy formularz *PictureViewer*, a następnie wybierz przycisk **OK** .

    >[!NOTE]
    >Jeśli szablon **aplikacji Windows Forms (.NET Framework)** nie jest widoczny, użyj Instalator programu Visual Studio, aby zainstalować obciążenie **programistyczne dla programu .NET Desktop** .<br/><br/>![obciążenie Programowanie aplikacji klasycznych platformy .NET w Instalator programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz stronę [Instalowanie programu Visual Studio](../install/install-visual-studio.md) .

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Open Visual Studio 2019

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wprowadź lub wpisz *Windows Forms* w polu wyszukiwania. Następnie wybierz pozycję **pulpit** z listy **Typ projektu** .

   Po zastosowaniu filtru **Typ projektu** wybierz szablon **aplikacja Windows Forms (.NET Framework)** dla obu C# lub Visual Basic, a następnie wybierz przycisk **dalej**.

   ![Wybierz szablon Visual Basic C# lub dla aplikacji Windows Forms (.NET Framework).](./media/create-new-project-search-winforms-filtered.png)

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

Program Visual Studio tworzy rozwiązanie dla aplikacji. Rozwiązanie działa jako kontener dla wszystkich projektów i plików wymaganych przez aplikację. Te warunki zostaną omówione bardziej szczegółowo w dalszej części tego samouczka.

## <a name="about-the-windows-forms-app-project"></a>Informacje o projekcie aplikacji Windows Forms

1. Środowisko deweloperskie zawiera trzy okna: okno główne, **Eksplorator rozwiązań**i okno **Właściwości** .

     Jeśli brakuje któregoś z tych okienek, możesz przywrócić domyślny układ okna. Na pasku menu wybierz **okno** > **Resetowanie układu okna**.

     Możesz również wyświetlić okna przy użyciu poleceń menu. Na pasku menu wybierz polecenie **wyświetl** > **okno właściwości** lub **Eksplorator rozwiązań**.

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

     przycisk ![Zapisz cały pasek narzędzi](../ide/media/express_iconsaveall.png)<br/>
     Przycisk ***Zapisz wszystkie*** *paski narzędzi*

     Program Visual Studio automatycznie wypełnia nazwę folderu i nazwę projektu, a następnie zapisuje projekt w folderze projektów.

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 2. Uruchamianie aplikacji](../ide/step-2-run-your-program.md)** .

* Aby powrócić do tematu przeglądu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
