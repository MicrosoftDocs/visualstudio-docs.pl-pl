---
title: Krok 1. Utwórz projekt Windows Forms aplikacji
ms.date: 03/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ccb92fbe04d9a867cec308e1e4819fa96023ad4
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515223"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Krok 1. Utwórz projekt Windows Forms aplikacji

Kiedy tworzysz przeglądarki obrazów, pierwszym krokiem jest utworzenie projektu aplikacji formularzy Windows.

 > [!TIP]
 > ![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 1](http://go.microsoft.com/fwlink/?LinkId=205209) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# -1 wideo](http://go.microsoft.com/fwlink/?LinkId=205199). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Open Visual Studio 2017

1. Na pasku menu wybierz **pliku** > **New** > **projektu**. Okno dialogowe powinno wyglądać następująco.

     ![Okno dialogowe nowego projektu](../ide/media/newprojectdialogcallouts.png)<br/>
***Nowy projekt** okno dialogowe*

2. Wybierz opcję **Visual C#**  lub **języka Visual Basic** w lewej części **nowy projekt** okno dialogowe.

3. Na liście szablonów wybierz **aplikacji programu Windows Forms (.NET Framework)**. Nazwij nowy formularz **PictureViewer**, a następnie wybierz **OK** przycisku.

    >[!NOTE]
    >Jeśli nie widzisz **aplikacji programu Windows Forms (.NET Framework)** szablon, użyj Instalatora programu Visual Studio, aby zainstalować **programowanie aplikacji klasycznych dla platformy .NET** obciążenia.<br/><br/>![Obciążenie programowanie aplikacji klasycznych dla platformy .NET w Instalatorze programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz [Zainstaluj program Visual Studio](../install/install-visual-studio.md) strony.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Open Visual Studio 2019

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

   ![Wyświetlanie w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na **Utwórz nowy projekt** oknie wprowadź lub wpisz *Windows Forms* w polu wyszukiwania. Następnie wybierz pozycję **języka Visual Basic** od języka, a następnie wybierz **Windows** z listy Platform. 

   Po zastosowaniu filtrów języka i platformy, wybierz **aplikacji programu Windows Forms (.NET Framework)** szablonu, a następnie wybierz **dalej**.

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

1. W **konfigurowania nowego projektu** oknie wpisz lub wprowadź *HelloWorld* w **Nazwa projektu** pole. Następnie wybierz **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" nazwij swój projekt "HelloWorld"](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

::: moniker-end

Program Visual Studio tworzy rozwiązanie dla Twojego programu. To rozwiązanie działa jako kontener dla wszystkich projektów i plików wymaganych przez program. Te zwroty zostaną wyjaśnione bardziej szczegółowo w dalszej części tego samouczka.

## <a name="about-the-windows-forms-application-project"></a>Temat projektu aplikacja interfejsu Windows Forms

1. Środowisko projektowe zawiera trzy okna: główne okno **Eksploratora rozwiązań**i **właściwości** okna.

     Jeśli brakuje któregokolwiek z tych okien, Przywróć domyślny układ okna, na pasku menu, wybierając **okna** > **Zresetuj układ okna**. Można również wyświetlić okna przy użyciu poleceń menu. Na pasku menu wybierz **widoku** > **okno właściwości** lub **Eksploratora rozwiązań**. Jeśli inne okna są otwarte, zamknij je, wybierając **Zamknij** (przycisku w ich prawym górnym rogu x).

    ::: moniker range="vs-2017"

    - **Okno główne** w tym oknie wykonasz większość swojej pracy, takich jak praca z formularzami i Edycja kodu. Okno przedstawia formularz w **Edytor formularzy**. W górnej części okna **strona startowa** kartę i **Form1.cs [projekt]** karty są wyświetlane. (W języku Visual Basic nazwa karty kończy się *.vb* zamiast *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    - **Okno główne** w tym oknie wykonasz większość swojej pracy, takich jak praca z formularzami i Edycja kodu. Okno przedstawia formularz w **Edytor formularzy**.

    ::: moniker-end

    - **Okno Eksploratora rozwiązań** w tym oknie można przeglądać i nawigować do wszystkich elementów w rozwiązaniu. Po wybraniu pliku, zawartość **właściwości** okna zmiany. Jeśli otworzysz plik kodu (którego nazwa kończy się na *.cs* w elemencie wizualnym C# i *.vb* w języku Visual Basic), pojawi się plik kodu lub Projektant pliku kodu. Projektant jest powierzchnią wizualną, na którym można dodać formanty, takie jak przyciski i listy. Formularzy programu Visual Studio Projektant nazywa **Windows Forms Designer**.

    - **Okno właściwości** w tym oknie można zmienić właściwości elementów, które wybrano w innych oknach. Na przykład, jeśli wybierzesz Form1, możesz zmienić jego tytuł przez ustawienie **tekstu** właściwości, na które można zmienić kolor tła, ustawiając **Backcolor** właściwości.

    > [!NOTE]
    > W pierwszym wierszu **Eksploratora rozwiązań** pokazuje **rozwiązanie "PictureViewer" (1 projekt)**, co oznacza, że tworzone rozwiązanie programu Visual Studio. To rozwiązanie może zawierać więcej niż jeden projekt, ale na razie będziesz pracować z rozwiązaniami, które zawierają tylko jeden projekt.

1. Na pasku menu wybierz **pliku** > **Zapisz wszystko**.

     Jako alternatywę, wybierz **Zapisz wszystko** przycisk na pasku narzędzi na następującej ilustracji pokazano.

     ![Zapisz wszystkie przyciski paska narzędzi](../ide/media/express_iconsaveall.png)<br/>
     ***Zapisz wszystko** przycisku paska narzędzi*

     Program Visual Studio automatycznie wypełnia nazwę folderu i nazwę projektu, a następnie zapisuje projekt w Twoim folderze projektów.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 2: Uruchom program](../ide/step-2-run-your-program.md).

- Aby powrócić do tematu przeglądu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Zobacz także

- [Tworzenie nowego formularza Windows](/dotnet/framework/winforms/creating-a-new-windows-form/)