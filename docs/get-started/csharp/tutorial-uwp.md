---
title: 'Tworzenie aplikacji platformy uniwersalnej systemu Windows (UWP) w programie Visual Studio i C #'
description: 'Tworzenie aplikacji platformy uniwersalnej systemu wizowego w programie Visual Studio za pomocą kodów XAML i C #'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580003"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Samouczek: Utwórz pierwszą uniwersalną aplikację platformy systemu Windows w programie Visual Studio za pomocą&#35; XAML i C

W tym wprowadzeniu do zintegrowanego środowiska programistycznego programu Visual Studio (IDE) utworzysz aplikację "Hello World", która działa na dowolnym urządzeniu z systemem Windows 10. W tym celu należy użyć szablonu projektu platformy uniwersalnej systemu Windows (UWP), języka XAML (Extensible Application Markup Language) i języka programowania C#.

::: moniker range="vs-2017"
Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.
::: moniker-end
::: moniker range="vs-2019"
Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.
::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt platformy uniwersalnej systemu Windows. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodasz!

::: moniker range="vs-2017"
1. Otwórz program Visual Studio.

1. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Visual C#,** a następnie wybierz pozycję **System Uniwersalny systemu Windows**. W środkowym okienku wybierz pozycję **Pusta aplikacja (uniwersalny system Windows).** Następnie nazwij projekt *HelloWorld* i wybierz **PRZYCISK OK**.

   ![Szablon projektu uniwersalnego systemu Windows w oknie dialogowym Nowy projekt w programie Visual Studio IDE](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu projektu **Pusta aplikacja (uniwersalny system Windows),** kliknij łącze **Otwórz instalator programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.**<br><br>![Kliknij łącze Otwórz instalator programu Visual Studio w oknie dialogowym Nowy projekt](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Uruchamia instalator programu Visual Studio. Wybierz obciążenie **deweloperów platformy uniwersalnej systemu Windows,** a następnie wybierz pozycję **Modyfikuj**.<br><br>![Obciążenie deweloperskie platformy systemu Windows w Instalatorze programu Visual Studio](media/uwp-dev-workload.png)

1. Zaakceptuj domyślną **wersję docelową** i ustawienia **wersji minimalnej** w oknie dialogowym **Nowy projekt platformy uniwersalnej systemu Windows.**

   ![Akceptowanie domyślnych ustawień wersji docelowej i wersji minimalnej w oknie dialogowym Nowy uniwersalny program Windows Platform Project](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otwórz program Visual Studio, a w oknie startowym wybierz pozycję **Utwórz nowy projekt**.

1. Na ekranie **Utwórz nowy projekt** wprowadź w polu wyszukiwania system *Uniwersalny Windows,* wybierz szablon C# dla **pustej aplikacji (system uniwersalny Systemu Windows),** a następnie wybierz pozycję **Dalej**.

   ![Zrzut ekranu przedstawiający Tworzenie nowego ekranu projektu](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu projektu **Pusta aplikacja (uniwersalny system Windows),** kliknij łącze **Zainstaluj więcej narzędzi i funkcji.**<br><br>![Kliknij łącze Zainstaluj więcej narzędzi i funkcji](media/vs-2019/uwp-not-finding.png)<br><br>Uruchamia instalator programu Visual Studio. Wybierz obciążenie **deweloperów platformy uniwersalnej systemu Windows,** a następnie wybierz pozycję **Modyfikuj**.<br><br>![Obciążenie deweloperskie platformy systemu Windows w Instalatorze programu Visual Studio](media/uwp-dev-workload.png)

1. Nadaj projektowi nazwę _HelloWorld_i wybierz pozycję **Utwórz**.

   ![Konfigurowanie ekranu projektu](media/vs-2019/uwp-configure-your-project.png)

1. Zaakceptuj domyślną **wersję docelową** i ustawienia **wersji minimalnej** w oknie dialogowym **Nowy projekt platformy uniwersalnej systemu Windows.**

   ![Akceptowanie domyślnych ustawień wersji docelowej i wersji minimalnej w oknie dialogowym Nowy uniwersalny program Windows Platform Project](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Jeśli jest to pierwszy raz, kiedy używasz programu Visual Studio do utworzenia aplikacji platformy uniwersalnej systemu wizowego, może pojawić się okno dialogowe **Ustawienia.** Wybierz **tryb dewelopera**, a następnie wybierz pozycję **Tak**.<br><br>
   > ![Włączanie trybu dewelopera w oknie dialogowym Ustawienia platformy uniwersalnej systemu i platformy uniwersalnej](media/enable-developer-mode.png)<br><br>Visual Studio instaluje dodatkowy pakiet trybu dewelopera dla Ciebie. Po zakończeniu instalacji pakietu zamknij okno dialogowe **Ustawienia.**

## <a name="create-the-application"></a>Tworzenie aplikacji

Nadszedł czas, aby zacząć się rozwijać. Dodasz kontrolkę przycisku, dodasz akcję do przycisku, a następnie uruchomisz aplikację "Hello World", aby zobaczyć, jak wygląda.

### <a name="add-a-button-to-the-design-canvas"></a>Dodawanie przycisku do kanwy Projekt

1. W **Eksploratorze rozwiązań**kliknij dwukrotnie pozycję *MainPage.xaml,* aby otworzyć widok podzielony.

   ::: moniker range="vs-2017"
   ![Otwórz plik MainPage.xaml w Eksploratorze rozwiązań ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Otwórz plik MainPage.xaml w Eksploratorze rozwiązań](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Istnieją dwa **okienka: Projektant XAML**, który zawiera kanwę projektu i **Edytor XAML**, gdzie można dodać lub zmienić kod.

   ![Okienko Projektanta XAML w edytorze XAML](media/uwp-xaml-editor.png)

1. Wybierz **przybornik,** aby otworzyć okno wysuwu przybornika.

   ![Kliknij przybornik, aby otworzyć okno wysuwu przybornika](media/uwp-toolbox.png)

   (Jeśli nie widzisz opcji **Przybornik,** możesz ją otworzyć na pasku menu. Aby to zrobić, wybierz pozycję **Wyświetl** > **pasek narzędzi**. Możesz też **nacisnąć klawisze Ctrl**+**Alt**+**X.**

1. Kliknij ikonę **Przypnij,** aby zadokować okno Przybornik.

   ![Kliknij ikonę Przypnij, aby zadokować okno Przybornik](media/uwp-toolbox-autohide.png)

1. Kliknij kontrolka **Przycisk,** a następnie przeciągnij go na kanwę projektu.

   ![Kliknij kontrolka Przycisk i przeciągnij go na kanwę Projektu](media/uwp-toolbox-add-button-control.png)

   Jeśli spojrzysz na kod w **Edytorze XAML,** zobaczysz, że przycisk został tam dodany:

   ![Kliknij kontrolka Przycisk i przeciągnij go na kanwę Projektu](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Dodawanie etykiety do przycisku

1. W **edytorze XAML**zmień wartość zawartości przycisku z "Button" na "Hello World!"

   ![Zmienianie wartości zawartości przycisku na Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

1. Należy zauważyć, że przycisk w **Projektancie XAML** również się zmienia.

   ![Przycisk zmieni się na Hello World na kanwie projektowej](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Dodawanie procedury obsługi zdarzeń

"Program obsługi zdarzeń" brzmi skomplikowanie, ale to tylko inna nazwa dla kodu, który jest wywoływany, gdy zdarzenie się dzieje. W tym przypadku dodaje akcję do "Hello World!" Edytuj...

1. Kliknij dwukrotnie kontrolka przycisku na kanwie projektu.

1. Edytuj kod obsługi zdarzeń w *MainPage.xaml.cs*, strona zakodowana.

   Oto, gdzie robi się ciekawie. Domyślny program obsługi zdarzeń wygląda następująco:

   ![Domyślny program obsługi zdarzeń Button_Click ](media/uwp-button-click-code.png)

   Zmieńmy to, więc wygląda to tak:

   ![Nowy program obsługi zdarzeń asynchronii Button_Click ](media/uwp-add-hello-world-async-code.png)

   Oto kod do kopiowania i wklejenia:

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

#### <a name="what-did-we-just-do"></a>Co po prostu zrobiliśmy?

Kod używa niektórych interfejsów API systemu Windows do utworzenia obiektu syntezy mowy, a następnie nadaje mu tekst do powiedzenia. (Aby uzyskać więcej `SpeechSynthesis`informacji <xref:System.Speech.Synthesis>na temat korzystania , zobacz .)

## <a name="run-the-application"></a>Uruchamianie aplikacji


::: moniker range="vs-2017"
Nadszedł czas, aby zbudować, wdrożyć i uruchomić aplikację platformy uniwersalnej systemu Windows "Hello World", aby zobaczyć, jak wygląda i brzmi. Oto jak to zrobić.

1. Użyj przycisku Odtwórz (ma tekst **Local Machine**), aby uruchomić aplikację na komputerze lokalnym.

   ![Kliknij pozycję Komputer lokalny, aby uruchomić i debugować aplikację platformy uniwersalnej systemu Windows](media/uwp-start-or-debug.png)

   (Alternatywnie można wybrać **debugowanie** > **start debugowania** z paska menu lub naciśnij klawisz F5, aby uruchomić aplikację).

1. Wyświetl aplikację, która pojawia się wkrótce po zniknięciu ekranu powitalnego. Aplikacja powinna wyglądać podobnie do tego:

   ![Aplikacja platformy uniwersalnej systemu Windows "Hello World"](media/uwp-hello-world-app.png)

1. Kliknij przycisk **Witaj w świecie.**

   Twoje urządzenie z systemem Windows 10 dosłownie powie: "Cześć, świat!"

1. Aby zamknąć aplikację, kliknij przycisk **Zatrzymaj debugowanie** na pasku narzędzi. (Alternatywnie wybierz **debugowanie** > **Zatrzymaj debugowanie** z paska menu lub naciśnij klawisze Shift+F5).

::: moniker-end
::: moniker range=">=vs-2019"
Nadszedł czas, aby zbudować, wdrożyć i uruchomić aplikację platformy uniwersalnej systemu Windows "Hello World", aby zobaczyć, jak wygląda i brzmi. Oto jak to zrobić.

1. Użyj przycisku Odtwórz (ma tekst **Local Machine**), aby uruchomić aplikację na komputerze lokalnym.

   ![Kliknij pozycję Komputer lokalny, aby uruchomić i debugować aplikację platformy uniwersalnej systemu Windows](media/uwp-start-or-debug.png)

   (Alternatywnie można wybrać **debugowanie** > **start debugowania** z paska menu lub naciśnij klawisz F5, aby uruchomić aplikację).

1. Wyświetl aplikację, która pojawia się wkrótce po zniknięciu ekranu powitalnego. Aplikacja powinna wyglądać podobnie do tego:

   ![Aplikacja platformy uniwersalnej systemu Windows "Hello World"](media/vs-2019/uwp-hello-world-app.png)

1. Kliknij przycisk **Witaj w świecie.**

   Twoje urządzenie z systemem Windows 10 dosłownie powie: "Cześć, świat!"

1. Aby zamknąć aplikację, kliknij przycisk **Zatrzymaj debugowanie** na pasku narzędzi. (Alternatywnie wybierz **debugowanie** > **Zatrzymaj debugowanie** z paska menu lub naciśnij klawisze Shift+F5).

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka! Mamy nadzieję, że poznaliście podstawy dotyczące platformy uniwersalnej systemu i środowiska IDE programu Visual Studio. Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Tworzenie interfejsu użytkownika](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Zobacz też

- [Omówienie platformy uniwersalnej systemu i platformy uniwersalnej systemu](/windows/uwp/get-started/universal-application-platform-guide)
- [Pobieranie próbek aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu](/windows/uwp/get-started/get-uwp-app-samples)