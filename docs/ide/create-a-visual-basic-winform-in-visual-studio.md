---
title: Tworzenie aplikacji Windows Forms za pomocą języka Visual Basic
description: Dowiedz się, jak utworzyć aplikację Formularze systemu Windows w programie Visual Studio za pomocą programu Visual Basic krok po kroku.
ms.date: 09/27/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8be3edaaab970dab7ef41bd8bce75c84bac54a2e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "71681585"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Tworzenie aplikacji Formularze systemu Windows w programie Visual Studio za pomocą języka Visual Basic

W tym krótkim wstępie do zintegrowanego środowiska programistycznego programu Visual Studio (IDE) utworzysz prostą aplikację języka Visual Basic, która ma interfejs użytkownika (UI) oparty na systemie Windows.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz [Personalizuj ide programu Visual Studio i edytora](../ide/quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak to zrobić.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji języka Visual Basic. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodasz.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń pozycję **Visual Basic**, a następnie wybierz pozycję Pulpit **systemu Windows**. W środkowym okienku wybierz pozycję **Windows Forms App (.NET Framework)**. Następnie nazwij plik `HelloWorld`.

     Jeśli nie widzisz szablonu projektu **aplikacji Windows Forms (.NET Framework),** anuluj z okna dialogowego **Nowy projekt** i z górnego paska menu wybierz pozycję **Narzędzia** > **Pobierz narzędzia i funkcje**. Uruchamia instalator programu Visual Studio. Wybierz obciążenie **programistyczne dla komputerów .NET,** a następnie wybierz pozycję **Modyfikuj**.

     ![Obciążenie rdzenia .NET w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wybierz szablon Aplikacji **Formularze systemu Windows (NET Framework)** dla języka Visual Basic.

   (Jeśli wolisz, możesz zawęzić wyszukiwanie, aby szybko przejść do żądanego szablonu. Na przykład wprowadź lub wpisz *aplikację Windows Forms w* polu wyszukiwania. Następnie wybierz pozycję **Visual Basic** z listy Język, a następnie wybierz pozycję **Windows** z listy Platformy).  

   ![Wybieranie szablonu języka Visual Basic dla aplikacji Windows Forms App (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli nie jest wyświetlany szablon **aplikacji Windows Forms App (.NET Framework),** można go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalatorze programu Visual Studio wybierz zadanie **tworzenia pulpitu .NET.**
   >
   > ![Obciążenie rdzenia .NET w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Utwórz projekt".](#create-a-project)

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *helloworld* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Skonfiguruj nowy projekt" nazwij swój projekt "HelloWorld"](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu języka Visual Basic i nazewnie pliku program Visual Studio otworzy formularz. Formularz jest interfejsem użytkownika systemu Windows. Utworzymy aplikację "Hello World", dodając formanty do formularza, a następnie uruchomimy aplikację.

### <a name="add-a-button-to-the-form"></a>Dodawanie przycisku do formularza

1. Kliknij **pozycję Przybornik,** aby otworzyć okno wysuwu przybornika.

     ![Kliknij przybornik, aby otworzyć okno Przybornik](../ide/media/vb-toolbox-toolwindow.png)

     (Jeśli nie widzisz opcji wysuwania **przybornika,** możesz ją otworzyć na pasku menu. Aby to zrobić, **Wyświetl** > **przybornik**. Możesz też **nacisnąć klawisze Ctrl**+**Alt**+**X.**

1. Kliknij ikonę **Przypnij,** aby zadokować okno **Przybornik.**

     ![Kliknij ikonę Przypnij, aby przypiąć okno Przybornika do środowiska IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Kliknij kontrolka **Przycisk,** a następnie przeciągnij go na formularz.

     ![Dodawanie przycisku do formularza](../ide/media/vb-add-a-button-to-form1.png)

1. W sekcji **Wygląd** (lub w sekcji **Czcionki)** okna `Click this` **Właściwości** wpisz , a następnie naciśnij klawisz **Enter**.

     ![Dodawanie tekstu do przycisku w formularzu](../ide/media/vb-button-control-text.png)

     (Jeśli nie widzisz okna **Właściwości,** możesz otworzyć je na pasku menu. Aby to zrobić, kliknij pozycję **Okno Wyświetl** > **właściwości**. Możesz też nacisnąć **klawisz F4**.)

1. W sekcji **Projektowanie** okna **Właściwości** zmień nazwę z **Button1** na `btnClickThis`, a następnie naciśnij **klawisz Enter**.

     ![Dodawanie funkcji do przycisku w formularzu](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Jeśli lista została alfabetycznie w oknie **Właściwości,** **przycisk1** pojawi się w sekcji **(DataBindings).**

### <a name="add-a-label-to-the-form"></a>Dodawanie etykiety do formularza

Teraz, gdy dodaliśmy kontrolkę przycisku, aby utworzyć akcję, dodajmy kontrolkę etykiety, do których chcesz wysłać tekst.

1. Zaznacz **kontrolkę Etykieta** z okna **Przybornik,** a następnie przeciągnij ją na formularz i upuść pod przyciskiem **Kliknij tę.**

1. W sekcji **Projektowanie** lub **(DataBindings)** okna **Właściwości** zmień nazwę **Label1** na `lblHelloWorld`, a następnie naciśnij **klawisz Enter**.

### <a name="add-code-to-the-form"></a>Dodawanie kodu do formularza

1. W oknie **&#93;&#91;Projektu form 1.vb** kliknij dwukrotnie przycisk Kliknij **ten** przycisk, aby otworzyć okno **Form1.vb.**

      (Alternatywnie można rozwinąć **form1.vb** w **Eksploratorze rozwiązań,** a następnie kliknąć **form1**.)

1. W oknie **Form1.vb** między **wierszami** `lblHelloWorld.Text = "Hello World!"` **Podobs.**

     ![Dodawanie kodu do formularza](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **Start,** aby uruchomić aplikację.

     ![Kliknij przycisk Start, aby debugować i uruchomić aplikację](../ide/media/vb-click-start-hello-world.png)

   Wydarzy się kilka rzeczy. W programie Visual Studio IDE otworzy się okno **Narzędzia diagnostyczne,** a otworzy się również okno **Dane wyjściowe.** Ale poza IDE, pojawi się okno dialogowe **Form1.** Będzie zawierać kliknij **ten** przycisk i tekst, który mówi **Label1**.

1. Kliknij przycisk **Kliknij ten** przycisk w oknie dialogowym **Formularz1.** Zwróć uwagę, że tekst **Label1** zmienia się na **Hello World!**.

    ![Okno dialogowe Form1 z tekstem Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Zamknij okno dialogowe **Form1,** aby zatrzymać uruchamianie aplikacji.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Samouczek: Tworzenie przeglądarki obrazów](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków języka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Samouczki języka C#](/visualstudio/get-started/csharp/)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)
