---
title: 'Samouczek: tworzenie aplikacji platformy UWP przy użyciu Visual Studio & C #'
description: 'Tworzenie aplikacji platformy UWP w języku Visual Studio xaml i C #'
titleSuffix: ''
ms.custom: vs-acquisition, get-started, SEO-VS-2020
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2e89c58e3c0dca2b5d009a592d3f242646339f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390297"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Samouczek: tworzenie pierwszej aplikacji platforma uniwersalna systemu Windows w języku Visual Studio xaml i C&#35;

W tym wprowadzeniu do Visual Studio zintegrowanego środowiska projektowego (IDE) utworzysz aplikację "Hello world", która działa na dowolnym urządzeniu Windows 10 projektowym. W tym celu użyjesz szablonu projektu platformy platforma uniwersalna systemu Windows (UWP), Extensible Application Markup Language (XAML) i języka programowania C#.

::: moniker range="vs-2017"
Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.
::: moniker-end
::: moniker range="vs-2019"
Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.
::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt platforma uniwersalna systemu Windows projektu. Typ projektu zawiera wszystkie potrzebne pliki szablonów przed dodaniu czegokolwiek!

::: moniker range="vs-2017"
1. Otwórz program Visual Studio.

1. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

1. W lewym okienku okna dialogowego **Nowy** projekt rozwiń pozycję **Visual C#,** a następnie wybierz pozycję **Uniwersalne systemu Windows.** W środkowym okienku wybierz pozycję **Pusta aplikacja (uniwersalny system Windows).** Następnie nadaj projektowi *nazwę HelloWorld i* wybierz **przycisk OK.**

   > [!NOTE]
   > Upewnij się, że lokalizacja projektu źródłowego znajduje się na dysku w formacie **NTFS(New Technology File System),** takim jak dysk systemu operacyjnego. W przeciwnym razie mogą wystąpić problemy podczas budowania i uruchamiania projektu. 

   ![Szablon uniwersalnego projektu systemu Windows w oknie dialogowym Nowy projekt w Visual Studio IDE](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu projektu Pusta aplikacja **(uniwersalny** system Windows), kliknij **link** Otwórz Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt.<br><br>![Kliknij link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie **platforma uniwersalna systemu Windows dewelopera,** a następnie wybierz pozycję **Modyfikuj.**<br><br>![platforma uniwersalna systemu Windows tworzenia aplikacji w Instalator programu Visual Studio](media/uwp-dev-workload.png)

1. Zaakceptuj domyślne ustawienia **Wersja docelowa** i **Minimalna wersja** w **oknie dialogowym Nowy platforma uniwersalna systemu Windows projekt.**

   ![Zaakceptuj domyślne ustawienia Wersja docelowa i Minimalna wersja w oknie dialogowym Nowy platforma uniwersalna systemu Windows projekt](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otwórz Visual Studio, a następnie w oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

1. Na **ekranie Create a new project** (Tworzenie nowego projektu) wprowadź wartość Universal Windows (Uniwersalny system *Windows)* w polu wyszukiwania, wybierz szablon języka C# dla opcji Pusta aplikacja **(universal Windows),** a następnie wybierz pozycję **Next (Dalej).**

   ![Zrzut ekranu przedstawiający ekran Tworzenie nowego projektu](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu projektu **Pusta aplikacja (uniwersalny** system Windows), kliknij link Zainstaluj więcej narzędzi **i** funkcji.<br><br>![Kliknij link Zainstaluj więcej narzędzi i funkcji](media/vs-2019/uwp-not-finding.png)<br><br>Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie **platforma uniwersalna systemu Windows dewelopera,** a następnie wybierz pozycję **Modyfikuj.**<br><br>![platforma uniwersalna systemu Windows tworzenia aplikacji w Instalator programu Visual Studio](media/uwp-dev-workload.png)

1. Nadaj projektowi nazwę _HelloWorld_ i wybierz pozycję **Utwórz.**

   ![Ekran konfigurowania projektu](media/vs-2019/uwp-configure-your-project.png)

1. Zaakceptuj domyślne ustawienia **Wersja docelowa** i **Minimalna wersja** w **oknie dialogowym Nowy platforma uniwersalna systemu Windows projekt.**

   ![Zaakceptuj domyślne ustawienia Wersja docelowa i Minimalna wersja w oknie dialogowym Nowy platforma uniwersalna systemu Windows projekt](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Jeśli po raz pierwszy używasz programu Visual Studio do tworzenia aplikacji platformy uniwersalnej systemu Windows, **może** zostać wyświetlone okno dialogowe Ustawienia. Wybierz **pozycję Tryb dewelopera,** a następnie wybierz pozycję **Tak.**<br><br>
   > ![Włączanie trybu dewelopera w oknie dialogowym Ustawienia platformy uniwersalnej systemu Windows](media/enable-developer-mode.png)<br><br>Visual Studio instaluje dodatkowy pakiet trybu dewelopera. Po zakończeniu instalacji pakietu zamknij okno **dialogowe** Ustawienia.

## <a name="create-the-application"></a>Tworzenie aplikacji

Na razie należy rozpocząć tworzenie aplikacji. Dodasz kontrolkę przycisku, dodasz akcję do przycisku, a następnie uruchom aplikację "Hello world", aby zobaczyć, jak to wygląda.

### <a name="add-a-button-to-the-design-canvas"></a>Dodawanie przycisku do kanwy projektu

1. W **Eksplorator rozwiązań** kliknij dwukrotnie *pozycję MainPage.xaml,* aby otworzyć widok podzielony.

   ::: moniker range="vs-2017"
   ![Otwórz mainPage.xaml z Eksplorator rozwiązań ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Otwórz mainPage.xaml z Eksplorator rozwiązań](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Istnieją dwa okienka: projektant XAML **,** która zawiera kanwę projektu, i Edytor **XAML,** w którym można dodawać lub zmieniać kod.

   ![Okienko projektant XAML w edytorze XAML](media/uwp-xaml-editor.png)

1. Wybierz **pozycję Przybornik,** aby otworzyć okno wysuwu przybornika.

   ![Kliknij pozycję Przybornik, aby otworzyć okno wysuwu przybornika](media/uwp-toolbox.png)

   (Jeśli nie widzisz opcji **Przybornik,** możesz otworzyć ją na pasku menu. W tym celu wybierz pozycję **Wyświetl**  >  **pasek narzędzi.** Możesz też nacisnąć **klawisze Ctrl** + **Alt** + **X).**

1. Kliknij **ikonę Przypnij,** aby zadokować okno przybornika.

   ![Kliknij ikonę Przypnij, aby zadokować okno przybornika](media/uwp-toolbox-autohide.png)

1. Kliknij **kontrolkę Przycisk,** a następnie przeciągnij ją na kanwę projektu.

   ![Kliknij kontrolkę Przycisk i przeciągnij ją na kanwę Projektuj](media/uwp-toolbox-add-button-control.png)

   Jeśli przyjrzysz się kodowi w edytorze **XAML**, zobaczysz, że przycisk został tam również dodany:

   ![Przycisk Pokaż w edytorze XAML](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Dodawanie etykiety do przycisku

1. W **edytorze XAML** zmień wartość zawartości przycisku z "Button" na "Hello world!"

   ![Zmień wartość zawartości Przycisk na Hello world](media/uwp-change-button-text-in-xaml-code-window.png)

1. Zwróć uwagę, że przycisk w **projektant XAML** się również zmienia.

   ![Przycisk zmieni się na Hello world na kanwie projektu](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Dodawanie procedury obsługi zdarzeń

"Procedura obsługi zdarzeń" wydaje się skomplikowana, ale jest to po prostu inna nazwa dla kodu, który jest wywoływany w przypadku wystąpienia zdarzenia. W tym przypadku dodaje akcję do "Hello world!" Edytuj...

1. Kliknij dwukrotnie kontrolkę przycisku na kanwie projektu.

1. Edytuj kod procedury obsługi zdarzeń w *pliku MainPage.xaml.cs* na stronie kodu.

   Oto miejsca, w których coś się ciekawi. Domyślna procedura obsługi zdarzeń wygląda następująco:

   ![Domyślna procedura obsługi Button_Click zdarzeń ](media/uwp-button-click-code.png)

   Zmieńmy go, aby wyglądał następująco:

   ![Nowa procedura obsługi Button_Click asynchronicznego ](media/uwp-add-hello-world-async-code.png)

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

#### <a name="what-did-we-just-do"></a>Co właśnie zrobiliśmy?

Kod używa niektórych interfejsów API systemu Windows do utworzenia obiektu syntezy mowy, a następnie nadaje mu tekst do wypowiedź. (Aby uzyskać więcej informacji na temat korzystania `SpeechSynthesis` z programu , zobacz  <xref:System.Speech.Synthesis> ).

## <a name="run-the-application"></a>Uruchamianie aplikacji

::: moniker range="vs-2017"
Czas na skompilowanie, wdrożenie i uruchomienie aplikacji platformy UWP "Hello world", aby zobaczyć, jak wygląda i wygląda. Oto jak to zrobić.

1. Użyj przycisku Odtwarzania (ma on tekst **Komputer lokalny),** aby uruchomić aplikację na komputerze lokalnym.

   ![Kliknij pozycję Komputer lokalny, aby uruchomić i debugować aplikację platformy uniwersalnej systemu Windows](media/uwp-start-or-debug.png)

   (Alternatywnie możesz wybrać pozycję **Debuguj** > **Rozpocznij debugowanie** z paska menu lub naciśnij klawisz F5, aby uruchomić aplikację.

1. Wyświetl aplikację, która zostanie wyświetlona wkrótce po zniknięciu ekranu powitalnego. Aplikacja powinna wyglądać podobnie do tej:

   ![Aplikacja "Hello world" platformy uniwersalnej systemu Windows](media/uwp-hello-world-app.png)

1. Kliknij przycisk **Hello world** przycisku.

   Twoje Windows 10 będzie dosłownie powiedzieć "Hello, World!"

1. Aby zamknąć aplikację, kliknij przycisk **Zatrzymaj debugowanie** na pasku narzędzi. (Alternatywnie wybierz pozycję **Debuguj**  >  **Zatrzymaj debugowanie** na pasku menu lub naciśnij klawisze Shift+F5).

::: moniker-end
::: moniker range=">=vs-2019"
Czas na skompilowanie, wdrożenie i uruchomienie aplikacji platformy UWP "Hello world", aby zobaczyć, jak wygląda i wygląda. Oto jak to zrobić.

1. Użyj przycisku Odtwarzania (ma on tekst **Komputer lokalny),** aby uruchomić aplikację na komputerze lokalnym.

   ![Kliknij pozycję Komputer lokalny, aby uruchomić i debugować aplikację platformy uniwersalnej systemu Windows](media/uwp-start-or-debug.png)

   (Alternatywnie możesz wybrać pozycję **Debuguj** > **Rozpocznij debugowanie** z paska menu lub naciśnij klawisz F5, aby uruchomić aplikację.

1. Wyświetl aplikację, która zostanie wyświetlona wkrótce po zniknięciu ekranu powitalnego. Aplikacja powinna wyglądać podobnie do tej:

   ![Aplikacja "Hello world" platformy uniwersalnej systemu Windows](media/vs-2019/uwp-hello-world-app.png)

1. Kliknij przycisk **Hello world** przycisku.

   Twoje Windows 10 będzie dosłownie powiedzieć "Hello, World!"

1. Aby zamknąć aplikację, kliknij przycisk **Zatrzymaj debugowanie** na pasku narzędzi. (Alternatywnie wybierz pozycję **Debuguj**  >  **Zatrzymaj debugowanie** na pasku menu lub naciśnij klawisze Shift+F5).

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka! Mamy nadzieję, że wiesz już kilka podstawowych informacji na temat platformy uniwersalnej systemu Windows i Visual Studio IDE. Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Tworzenie interfejsu użytkownika](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Zobacz też

- [Omówienie platformy UWP](/windows/uwp/get-started/universal-application-platform-guide)
- [Pobierz przykłady aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/get-started/get-uwp-app-samples)
