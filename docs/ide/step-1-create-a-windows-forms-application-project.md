---
title: 'Krok 1: Tworzenie projektu aplikacji Windows Forms'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579913"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Krok 1: Tworzenie projektu aplikacji Windows Forms

Podczas tworzenia przeglądarki obrazów pierwszym krokiem jest utworzenie projektu aplikacji Windows Forms.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Otwórz program Visual Studio 2017

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. Okno dialogowe powinno wyglądać podobnie do poniższego zrzutu ekranu.

     ![Nowe okno dialogowe projektu](../ide/media/newprojectdialogcallouts.png)<br/>***Okno*** *dialogowe* Nowy projekt

2. Po lewej stronie okna dialogowego **Nowy projekt** wybierz pozycję **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję Pulpit **systemu Windows**.

3. Na liście szablonów projektów wybierz pozycję **Windows Forms App (.NET Framework).** Nazwij nowy formularz *PictureViewer*, a następnie wybierz przycisk **OK.**

    >[!NOTE]
    >Jeśli nie widzisz szablonu **aplikacji Windows Forms App (.NET Framework),** użyj Instalatora programu Visual Studio, aby zainstalować obciążenie **programowe .NET dla deweloperów pulpitu.**<br/><br/>![Obciążenie programistyczne pulpitu .NET w Instalatorze programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz stronę [Instalowanie programu Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Otwórz visual studio 2019

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *formularze systemu Windows* w polu wyszukiwania. Następnie wybierz pozycję **Pulpit** z listy **Typu projektu.**

   Po zastosowaniu filtru **typu projektu** wybierz szablon aplikacji Windows Forms **App (.NET Framework)** dla języka C# lub Visual Basic, a następnie wybierz pozycję **Dalej**.

   ![Wybierz szablon C# lub Visual Basic dla aplikacji Windows Forms App (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji Windows Forms App (.NET Framework),** możesz go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalatorze programu Visual Studio wybierz zadanie **tworzenia pulpitu .NET.**
   >
   > ![Obciążenie rdzenia .NET w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie.

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *pictureviewer* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

::: moniker-end

Visual Studio tworzy rozwiązanie dla aplikacji. Rozwiązanie działa jako kontener dla wszystkich projektów i plików potrzebnych w aplikacji. Terminy te zostaną wyjaśnione bardziej szczegółowo w dalszej części tego samouczka.

## <a name="about-the-windows-forms-app-project"></a>Projekt aplikacji Formularze systemu Windows — informacje

1. Środowisko programistyczne zawiera trzy okna: okno główne, **Eksplorator rozwiązań**i okno **Właściwości.**

     Jeśli brakuje któregokolwiek z tych okien, można przywrócić domyślny układ okna. Na pasku menu wybierz pozycję**Układ okna resetowania** **okna** > .

     Okna można również wyświetlać za pomocą poleceń menu. Na pasku menu wybierz polecenie **Wyświetl** > **okno właściwości** lub **Eksplorator rozwiązań**.

     Jeśli inne okna są otwarte, zamknij je, wybierając przycisk **Zamknij** (x) w prawym górnym rogu.

    ::: moniker range="vs-2017"

    * **Okno główne** W tym oknie wykonasz większość pracy, na przykład pracę z formularzami i edytowanie kodu. W oknie jest wyświetlany formularz w **Edytorze formularzy**. W górnej części okna zostanie wyświetlona karta **Strona początkowa** i **karta Form1.cs [Projekt].** (W języku Visual Basic nazwa karty kończy się na *.vb* zamiast *.cs).)*

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Okno główne** W tym oknie wykonasz większość pracy, na przykład pracę z formularzami i edytowanie kodu. W oknie jest wyświetlany formularz w **Edytorze formularzy**.

    ::: moniker-end

    * **Okno Eksploratora rozwiązań** W tym oknie można wyświetlić i przejść do wszystkich elementów w rozwiązaniu.

    Jeśli wybierzesz plik, zawartość okna **Właściwości** ulegnie zmianie. Jeśli otworzysz plik kodu (który kończy się na *cs* w języku C# i *.vb* w języku Visual Basic), pojawi się plik kodu lub projektant pliku kodu. Projektant to powierzchnia wizualna, na której można dodawać formanty, takie jak przyciski i listy. W przypadku formularzy programu Visual Studio projektant nosi nazwę **Projektanta formularzy systemu Windows**.

    * **Okno Właściwości** W tym oknie można zmienić właściwości elementów, które można wybrać w innych oknach. Na przykład, jeśli wybierzesz Form1, można zmienić jego tytuł, ustawiając **Text** właściwości i można zmienić kolor tła, ustawiając **Backcolor** właściwości.

      > [!NOTE]
      > Górna linia w **Eksploratorze rozwiązań** pokazuje **rozwiązanie "PictureViewer" (1 projekt),** co oznacza, że program Visual Studio utworzył rozwiązanie dla Ciebie. Rozwiązanie może zawierać więcej niż jeden projekt, ale na razie będziesz pracować z rozwiązaniami, które zawierają tylko jeden projekt.

1. Na pasku menu wybierz pozycję Zapisz**wszystko** **.** > 

     Alternatywnie wybierz przycisk **Zapisz wszystko** na pasku narzędzi, który pokazano na poniższej ilustracji.

     ![Przycisk Zapisz wszystkie paski narzędzi](../ide/media/express_iconsaveall.png)<br/>
     ***Przycisk Zapisz wszystkie*** *paski narzędzi*

     Program Visual Studio automatycznie wypełnia nazwę folderu i nazwę projektu, a następnie zapisuje projekt w folderze projektów.

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 2: Uruchamianie aplikacji](../ide/step-2-run-your-program.md)**.

* Aby powrócić do tematu przeglądu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
