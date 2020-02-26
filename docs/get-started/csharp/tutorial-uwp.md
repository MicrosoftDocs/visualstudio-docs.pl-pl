---
title: Tworzenie aplikacji platforma uniwersalna systemu Windows (platformy UWP) za pomocą programu Visual Studio iC#
description: Tworzenie aplikacji platformy UWP w programie Visual Studio przy użyciu języka XAML iC#
titleSuffix: ''
ms.custom: seodec18, get-started
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8be56581374aefbef41a5173836d1189cceff290
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580003"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Samouczek: Tworzenie pierwszej aplikacji platforma uniwersalna systemu Windows w programie Visual Studio za pomocą języków XAML i C&#35;

W tym wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz aplikację "Hello world" działającą na dowolnym urządzeniu z systemem Windows 10. W tym celu należy użyć szablonu projektu platforma uniwersalna systemu Windows (platformy UWP), Extensible Application Markup Language (XAML) i języka C# programowania.

::: moniker range="vs-2017"
Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.
::: moniker-end
::: moniker range="vs-2019"
Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.
::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt platforma uniwersalna systemu Windows. Typ projektu jest dostarczany ze wszystkimi potrzebnymi plikami szablonu, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"
1. Otwórz program Visual Studio.

1. Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń pozycję **Wizualizacja C#** , a następnie wybierz opcję **uniwersalne systemu Windows**. W środkowym okienku wybierz pozycję **pusta aplikacja (uniwersalna platforma Windows)** . Następnie nazwij projekt *HelloWorld* i wybierz **przycisk OK**.

   ![Szablon uniwersalnego projektu systemu Windows w oknie dialogowym Nowy projekt w programie Visual Studio IDE](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu projektu **pusta aplikacja (uniwersalna systemu Windows)** , kliknij link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .<br><br>![kliknij link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Uruchamia Instalatora programu Visual Studio. Wybierz **platforma uniwersalna systemu Windows obciążenie programowaniem** , a następnie wybierz polecenie **Modyfikuj**.<br><br>![platforma uniwersalna systemu Windows obciążeń programistycznych Instalator programu Visual Studio](media/uwp-dev-workload.png)

1. Zaakceptuj domyślną **wersję docelową** i ustawienia **minimalnej wersji** w oknie dialogowym **Nowy projekt platforma uniwersalna systemu Windows** .

   ![Zaakceptuj domyślną wersję docelową i ustawienia minimalnej wersji w oknie dialogowym Nowy projekt platforma uniwersalna systemu Windows](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otwórz program Visual Studio, a następnie w oknie Start wybierz pozycję **Utwórz nowy projekt**.

1. Na ekranie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania *okna uniwersalne* , wybierz C# szablon **pustej aplikacji (uniwersalne systemu Windows)** , a następnie wybierz przycisk **dalej**.

   ![Zrzut ekranu przedstawiający ekran Tworzenie nowego projektu](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu projektu **pusta aplikacja (uniwersalna systemu Windows)** , kliknij link **Zainstaluj więcej narzędzi i funkcji** .<br><br>![kliknij link zainstaluj więcej narzędzi i funkcji](media/vs-2019/uwp-not-finding.png)<br><br>Uruchamia Instalatora programu Visual Studio. Wybierz **platforma uniwersalna systemu Windows obciążenie programowaniem** , a następnie wybierz polecenie **Modyfikuj**.<br><br>![platforma uniwersalna systemu Windows obciążeń programistycznych Instalator programu Visual Studio](media/uwp-dev-workload.png)

1. Nadaj projektowi nazwę, _HelloWorld_i wybierz pozycję **Utwórz**.

   ![Konfigurowanie ekranu projektu](media/vs-2019/uwp-configure-your-project.png)

1. Zaakceptuj domyślną **wersję docelową** i ustawienia **minimalnej wersji** w oknie dialogowym **Nowy projekt platforma uniwersalna systemu Windows** .

   ![Zaakceptuj domyślną wersję docelową i ustawienia minimalnej wersji w oknie dialogowym Nowy projekt platforma uniwersalna systemu Windows](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Jeśli używasz programu Visual Studio po raz pierwszy do utworzenia aplikacji platformy UWP, może pojawić się okno dialogowe **Ustawienia** . Wybierz **Tryb dewelopera**, a następnie wybierz pozycję **tak**.<br><br>
   > ![włączyć tryb dewelopera w oknie dialogowym Ustawienia platformy UWP](media/enable-developer-mode.png)<br><br>Program Visual Studio instaluje dodatkowy pakiet trybu dewelopera. Po zakończeniu instalacji pakietu Zamknij okno dialogowe **Ustawienia** .

## <a name="create-the-application"></a>Tworzenie aplikacji

Rozpoczęcie tworzenia aplikacji jest czasochłonne. Dodasz kontrolkę Button, dodasz akcję do przycisku, a następnie uruchomisz aplikację "Hello world", aby zobaczyć, jak wygląda.

### <a name="add-a-button-to-the-design-canvas"></a>Dodawanie przycisku do kanwy projektowania

1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję *MainPage. XAML* , aby otworzyć widok podzielony.

   ::: moniker range="vs-2017"
   ![Otwórz MainPage. XAML z Eksplorator rozwiązań ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Otwórz MainPage. XAML z Eksplorator rozwiązań](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Istnieją dwa okienka: **Projektant XAML**, który obejmuje kanwę projektu i **Edytor XAML**, w którym można dodać lub zmienić kod.

   ![Okienko projektant XAML w edytorze XAML](media/uwp-xaml-editor.png)

1. Wybierz **Przybornik** , aby otworzyć okno wyskakujące Przybornik.

   ![Kliknij przycisk Przybornik, aby otworzyć okno podręczne przybornika](media/uwp-toolbox.png)

   (Jeśli nie widzisz opcji **przybornika** , możesz otworzyć ją z paska menu. Aby to zrobić, wybierz pozycję **wyświetl** > **pasku narzędzi**. Lub naciśnij **klawisze Ctrl**+**Alt**+**X**.)

1. Kliknij ikonę **pinezki** , aby zadokować okno Przybornik.

   ![Kliknij ikonę pinezki, aby zadokować okno przybornika](media/uwp-toolbox-autohide.png)

1. Kliknij kontrolkę **przycisk** , a następnie przeciągnij ją na kanwę projektowania.

   ![Kliknij kontrolkę przycisk i przeciągnij ją na kanwę projektu](media/uwp-toolbox-add-button-control.png)

   Jeśli zobaczysz kod w **Edytorze XAML**, zobaczysz, że przycisk został już dodany.

   ![Kliknij kontrolkę przycisk i przeciągnij ją na kanwę projektu](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Dodawanie etykiety do przycisku

1. W **Edytorze XAML**Zmień wartość zawartości przycisku z "Button" na "Hello World!"

   ![Zmień wartość zawartości przycisku na Hello world](media/uwp-change-button-text-in-xaml-code-window.png)

1. Zauważ, że przycisk w **Projektant XAML** zmienia się.

   ![Przycisk zostanie zmieniony na Hello world na kanwie projektu](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Dodawanie procedury obsługi zdarzeń

"Program obsługi zdarzeń" jest skomplikowany, ale jest to tylko inna nazwa kodu, który jest wywoływany, gdy wystąpi zdarzenie. W takim przypadku dodaje akcję do "Hello world!" Dodaj...

1. Kliknij dwukrotnie formant Button na kanwie projektowej.

1. Edytuj kod programu obsługi zdarzeń w *MainPage.XAML.cs*, stronie powiązanej z kodem.

   Tutaj znajdziesz interesujące rzeczy. Domyślna procedura obsługi zdarzeń wygląda następująco:

   ![Domyślny program obsługi zdarzeń Button_Click ](media/uwp-button-click-code.png)

   Zmieńmy ją, aby wyglądać następująco:

   ![Nowy program obsługi zdarzeń Button_Click asynchronicznej ](media/uwp-add-hello-world-async-code.png)

   Oto kod do skopiowania i wklejenia:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

#### <a name="what-did-we-just-do"></a>Co robimy?

Kod używa niektórych interfejsów API systemu Windows, aby utworzyć obiekt syntezy mowy, a następnie przekazać go do tekstu. (Aby uzyskać więcej informacji na temat korzystania z `SpeechSynthesis`, zobacz <xref:System.Speech.Synthesis>.)

## <a name="run-the-application"></a>Uruchamianie aplikacji


::: moniker range="vs-2017"
Czas na skompilowanie, wdrożenie i uruchomienie aplikacji platformy UWP "Hello world", aby zobaczyć, co wygląda i czego szuka. Poniżej przedstawiono sposób.

1. Użyj przycisku Odtwórz (ma tekst **komputer lokalny**), aby uruchomić aplikację na komputerze lokalnym.

   ![Kliknij pozycję maszyna lokalna, aby uruchomić i debugować aplikację platformy UWP](media/uwp-start-or-debug.png)

   (Możesz również wybrać **debuguj** > **rozpocząć debugowanie** z paska menu lub nacisnąć klawisz F5, aby uruchomić aplikację).

1. Wyświetl aplikację, która pojawia się wkrótce po usunięciu ekranu powitalnego. Aplikacja powinna wyglądać podobnie do tego:

   ![Aplikacja platformy UWP "Hello world"](media/uwp-hello-world-app.png)

1. Kliknij przycisk **Hello World** .

   Twoje urządzenie z systemem Windows 10 będzie dosłownie "Hello, World!"

1. Aby zamknąć aplikację, kliknij przycisk **Zatrzymaj debugowanie** na pasku narzędzi. (Alternatywnie wybierz **debuguj** > **Zatrzymaj debugowanie** z paska menu lub naciśnij klawisze Shift + F5).

::: moniker-end
::: moniker range=">=vs-2019"
Czas na skompilowanie, wdrożenie i uruchomienie aplikacji platformy UWP "Hello world", aby zobaczyć, co wygląda i czego szuka. Poniżej przedstawiono sposób.

1. Użyj przycisku Odtwórz (ma tekst **komputer lokalny**), aby uruchomić aplikację na komputerze lokalnym.

   ![Kliknij pozycję maszyna lokalna, aby uruchomić i debugować aplikację platformy UWP](media/uwp-start-or-debug.png)

   (Możesz również wybrać **debuguj** > **rozpocząć debugowanie** z paska menu lub nacisnąć klawisz F5, aby uruchomić aplikację).

1. Wyświetl aplikację, która pojawia się wkrótce po usunięciu ekranu powitalnego. Aplikacja powinna wyglądać podobnie do tego:

   ![Aplikacja platformy UWP "Hello world"](media/vs-2019/uwp-hello-world-app.png)

1. Kliknij przycisk **Hello World** .

   Twoje urządzenie z systemem Windows 10 będzie dosłownie "Hello, World!"

1. Aby zamknąć aplikację, kliknij przycisk **Zatrzymaj debugowanie** na pasku narzędzi. (Alternatywnie wybierz **debuguj** > **Zatrzymaj debugowanie** z paska menu lub naciśnij klawisze Shift + F5).

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Gratulujemy wykonanie kroków tego samouczka! Mamy nadzieję, że znasz kilka podstawowych informacji na temat platformy UWP i środowiska IDE programu Visual Studio. Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Tworzenie interfejsu użytkownika](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Zobacz też

- [PLATFORMY UWP — Omówienie](/windows/uwp/get-started/universal-application-platform-guide)
- [Pobierz przykłady aplikacji platformy UWP](/windows/uwp/get-started/get-uwp-app-samples)