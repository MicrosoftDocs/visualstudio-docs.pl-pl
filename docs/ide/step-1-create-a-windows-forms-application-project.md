---
title: Krok 1. Tworzenie projektu aplikacji Windows Forms
description: Dowiedz się, jak utworzyć Windows Forms aplikacji dla przeglądarki obrazów.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fccce125b66101b05544cba22b3724a8a40dc0f3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307742"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Krok 1. Tworzenie projektu aplikacji Windows Forms

Podczas tworzenia przeglądarki obrazów pierwszym krokiem jest utworzenie projektu aplikacji Windows Forms Aplikacji.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Open Visual Studio 2017

1. Na pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** Okno dialogowe powinno wyglądać podobnie do poniższego zrzutu ekranu.

     ![Okno dialogowe Nowy projekt](../ide/media/newprojectdialogcallouts.png)<br/>***Nowy projekt** _ pole _dialog projektowe*

2. Po lewej stronie okna **dialogowego Nowy** projekt wybierz pozycję **Visual C#** **lub Visual Basic**, a następnie wybierz pozycję **Windows Desktop.**

3. Na liście szablonów projektów wybierz pozycję **Windows Forms App (.NET Framework).** Nadaj noweowi *formularzowi nazwę PictureViewer,* a następnie wybierz **przycisk OK.**

    >[!NOTE]
    >Jeśli nie widzisz szablonu **Windows Forms App (.NET Framework),** użyj szablonu Instalator programu Visual Studio, aby zainstalować obciążenie tworzenie aplikacji klasycznych dla programu **.NET.**<br/><br/>![Obciążenie tworzenia aplikacji klasycznych dla programu .NET w Instalator programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz [stronę Visual Studio](../install/install-visual-studio.md) instalacji.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-visual-studio"></a>Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Tworzenie nowego projektu** wprowadź lub wpisz *Windows Forms* w polu wyszukiwania. Następnie wybierz pozycję **Desktop** z **listy Typ** projektu.

   Po zastosowaniu **filtru Project type** (Typ projektu) wybierz **szablon Windows Forms App (.NET Framework)** dla języka C# lub Visual Basic, a następnie wybierz pozycję **Next (Dalej).**

   ![Wybierz szablon aplikacji Visual Basic C# lub Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji Windows Forms (.NET Framework),** możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie można znaleźć tego,** czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalator programu Visual Studio wybierz obciążenie Wybierz tworzenie aplikacji **klasycznych dla programu .NET.**
   >
   > ![Obciążenie .NET Core w Instalator programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie.

1. W **oknie Konfigurowanie nowego projektu** wpisz lub wprowadź *PictureViewer* w **polu Nazwa** projektu. Następnie wybierz pozycję **Utwórz**.

::: moniker-end

Visual Studio tworzy rozwiązanie dla aplikacji. Rozwiązanie działa jako kontener dla wszystkich projektów i plików wymaganych przez aplikację. Te terminy zostaną bardziej szczegółowo wyjaśnione w dalszej części tego samouczka.

## <a name="about-the-windows-forms-app-project"></a>Informacje o projekcie Windows Forms App

1. Środowisko projektowe zawiera trzy okna: okno główne, **Eksplorator rozwiązań**, i **okno** Właściwości.

     Jeśli brakuje dowolnego z tych okien, możesz przywrócić domyślny układ okna. Na pasku menu wybierz pozycję **Układ**  >  **okna resetowania okna.**

     Okna można również wyświetlać za pomocą poleceń menu. Na pasku menu wybierz pozycję **Wyświetl** okno właściwości lub wybierz  >   **Eksplorator rozwiązań**.

     Jeśli jakiekolwiek inne okna są otwarte, zamknij je, wybierając przycisk **Zamknij** (x) w prawym górnym rogu.

    ::: moniker range="vs-2017"

    * **Okno główne** W tym oknie będziesz wykonać większość pracy, na przykład pracy z formularzami i edytowania kodu. W oknie zostanie pokazany formularz w **Edytorze formularzy.** W górnej części okna zostaną wyświetlone karty **Strona** startowa i **Form1.cs [Design].** (W Visual Basic nazwa karty kończy się *na .vb* zamiast *.cs.*

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Okno główne** W tym oknie będziesz wykonać większość pracy, na przykład pracy z formularzami i edytowania kodu. W oknie zostanie pokazany formularz w **Edytorze formularzy.**

    ::: moniker-end

    * **Eksplorator rozwiązań okno** W tym oknie można wyświetlać i przechodzić do wszystkich elementów w rozwiązaniu.

    Jeśli wybierzesz plik, zawartość okna **Właściwości zmieni** się. Jeśli otworzysz plik kodu (który kończy się na *.cs* w języku C# i *.vb* w języku Visual Basic), zostanie wyświetlony plik kodu lub projektant pliku kodu. Projektant to powierzchnia wizualna, na której można dodawać kontrolki, takie jak przyciski i listy. W Visual Studio formularzy projektant jest nazywany Projektant formularzy systemu Windows **.**

    * **okno Właściwości** W tym oknie można zmienić właściwości elementów wybieranych w innych oknach. Jeśli na przykład wybierzesz formularz Form1, możesz zmienić jego tytuł, ustawiając właściwość **Text,** a kolor tła można zmienić, ustawiając właściwość **Backcolor.**

      > [!NOTE]
      > W górnym wierszu **Eksplorator rozwiązań** przedstawiono rozwiązanie **"PictureViewer" (1 projekt),** co oznacza, Visual Studio rozwiązanie zostało utworzone automatycznie. Rozwiązanie może zawierać więcej niż jeden projekt, ale na razie będziesz pracować z rozwiązaniami, które zawierają tylko jeden projekt.

1. Na pasku menu wybierz pozycję **Plik**  >  **Zapisz wszystko.**

     Alternatywnie wybierz przycisk **Zapisz wszystko** na pasku narzędzi, który przedstawiono na poniższej ilustracji.

     ![Przycisk Zapisz wszystko na pasku narzędzi](../ide/media/express_iconsaveall.png)<br/>
     ***Zapisz wszystko** _ _toolbar przycisku*

     Visual Studio automatycznie wypełnia nazwę folderu i nazwę projektu, a następnie zapisuje projekt w folderze projektów.

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 2. Uruchamianie aplikacji.](../ide/step-2-run-your-program.md)**

* Aby wrócić do tematu z omówieniem, zobacz [Samouczek 1: tworzenie przeglądarki obrazów.](../ide/tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: tworzenie testu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
