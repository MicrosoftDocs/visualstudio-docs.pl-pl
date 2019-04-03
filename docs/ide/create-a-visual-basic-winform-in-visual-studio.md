---
title: Utwórz Windows Forms aplikacji za pomocą Visual Basic
description: Dowiedz się, jak tworzenie aplikacji Windows Forms w programie Visual Studio za pomocą Visual Basic, który krok po kroku.
ms.date: 03/23/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 511305bd335bfb982590db2c52c35fabbfc7b841
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58856490"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Utwórz Windows Forms aplikacji w programie Visual Studio za pomocą Visual Basic

W tym krótkie wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz prostą aplikację języka Visual Basic, która ma interfejs użytkownika oparty na Windows (UI).

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) strony, aby zainstalować go za darmo.

> [!NOTE]
> Niektóre zrzuty ekranu, w tym samouczku Użyj ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](../ide/quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku Visual Basic. Typ projektu zawiera wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **języka Visual Basic**, a następnie wybierz **pulpitu Windows**. W środkowym okienku wybierz **aplikacji programu Windows Forms (.NET Framework)**. Następnie Nazwij plik `HelloWorld`.

     Jeśli nie widzisz **aplikacji programu Windows Forms (.NET Framework)** projektu szablonu, Anuluj poza **nowy projekt** okna dialogowego pole, a następnie na pasku menu u góry wybierz **narzędzia**  >  **Pobierz narzędzia i funkcje**. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, wybierz **Modyfikuj**.

     ![Obciążenie platformy .NET core w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

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
   > Następnie należy wybrać **Modyfikuj** przycisku w Instalatorze programu Visual Studio. Może zostać wyświetlony monit, aby zapisać swoją pracę; Jeśli tak, należy to zrobić. Następnie wybierz pozycję **Kontynuuj** do zainstalowania z obciążeniem. Następnie wróć do kroku 2, w tym "[Utwórz projekt](#create-a-project)" procedury.

1. W **konfigurowania nowego projektu** oknie wpisz lub wprowadź *HelloWorld* w **Nazwa projektu** pole. Następnie wybierz **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" nazwij swój projekt "HelloWorld"](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu języka Visual Basic i nazwę pliku, programu Visual Studio otwiera formularz. Formularz jest interfejs użytkownika Windows. Utworzymy aplikację "Hello World" poprzez dodawanie formantów do formularza, a następnie uruchomimy aplikację.

### <a name="add-a-button-to-the-form"></a>Dodawanie przycisku do formularza

1. Kliknij przycisk **przybornika** można otworzyć okna wysuwanego przybornika.

     ![Kliknij przycisk przybornika, aby otworzyć okno przybornika](../ide/media/vb-toolbox-toolwindow.png)

     (Jeśli nie widzisz **przybornika** staną się opcji, możesz otworzyć, naciskając klawisz **Ctrl**+**Alt**+**X**.)

2. Kliknij przycisk **numeru Pin** ikonę, aby zadokować **przybornika** okna.

     ![Kliknij ikonę pinezki, aby przypiąć okno przybornika środowiska IDE](../ide/media/vb-pin-the-toolbox-window.png)

3. Kliknij przycisk **przycisk** sterowania, a następnie przeciągnij go do formularza.

     ![Dodawanie przycisku do formularza](../ide/media/vb-add-a-button-to-form1.png)

4. W **wygląd** sekcji (lub **czcionki** sekcji) z **właściwości** okna, typ `Click this`, a następnie naciśnij klawisz **Enter**.

     ![Dodawanie tekstu do przycisku w formularzu](../ide/media/vb-button-control-text.png)

     (Jeśli nie widzisz **właściwości** okna, możesz go otworzyć z paska menu. Aby to zrobić, kliknij przycisk **widoku** > **okno właściwości**. Lub naciśnij **F4**.)

5. W **projektowania** części **właściwości** okna, zmiana nazwy na podstawie **Button1** do `btnClickThis`, a następnie naciśnij klawisz **Enter**.

     ![Dodawanie funkcji do przycisku w formularzu](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Dodaj etykietę do formularza

Teraz, po dodaniu kontrolki przycisku, aby utworzyć akcję, możemy dodać kontrolkę typu etykieta do tekstu do wysłania.

1. Wybierz **etykiety** kontrolować z **przybornika** okna, a następnie przeciągnij go do formularza i upuść go pod **kliknij ten element** przycisku.

2. W **projektowania** części **właściwości** okna, zmiana nazwy na podstawie **Label1** do `lblHelloWorld`, a następnie naciśnij klawisz **Enter**.

### <a name="add-code-to-the-form"></a>Dodaj kod do formularza

1. W **Form1.vb &#91;projektowania&#93;**  okna, kliknij dwukrotnie **kliknij** przycisk, aby otworzyć **Form1.vb** okna.

      (Ewentualnie możesz rozwinąć **Form1.vb** w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Form1**.)

2. W **Form1.vb** okna, między **Sub prywatne** wiersza i **End Sub** wiersza (lub pomiędzy **Public Class Form1** wiersza i  **End Class** wiersza), wpisz następujący kod.

     ![Dodaj kod do formularza](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **Start** przycisk, aby uruchomić aplikację.

     ![Kliknij przycisk Uruchom, aby debugować i uruchamianie aplikacji](../ide/media/vb-click-start-hello-world.png)

   Wykonanych kilka działań. W programie Visual Studio IDE **narzędzia diagnostyczne** okno i **dane wyjściowe** okno zbyt. Ale poza IDE **Form1** pojawi się okno dialogowe. Będzie on zawierał swoje **kliknij** przycisk i tekst, który jest wyświetlany komunikat **Label1**.

2. Kliknij przycisk **kliknij** znajdujący się w **Form1** okno dialogowe. Należy zauważyć, że **Label1** tekst zmienia się na **Hello World!**.

    ![Formularz Form1 okno dialogowe, które zawiera tekst Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco Visual Basic i Visual Studio IDE. Jeśli chcesz delve głębiej, kontynuuj samouczek z **samouczki** części spisu treści.

## <a name="see-also"></a>Zobacz także

* [Szybki start: Tworzenie aplikacji konsoli w programie Visual Studio za pomocą Visual Basic](quickstart-visual-basic-console.md)
* [Dowiedz się więcej o technologii IntelliSense w języku Visual Basic](visual-basic-specific-intellisense.md)
