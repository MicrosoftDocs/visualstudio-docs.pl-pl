---
title: Tworzenie aplikacji platformy (systemu Windows UWP) Universal Windows z programem Visual Studio iC#
description: Tworzenie aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio przy użyciu XAML iC#
titleSuffix: ''
ms.custom: seodec18, get-started
ms.date: 03/11/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 557a87253b2fefe90fa83a06666a196128f64360
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322561"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Samouczek: Tworzenie pierwszej aplikacji Universal Windows Platform w programie Visual Studio przy użyciu XAML i C&#35;

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz aplikację "Hello World", która jest uruchamiana na dowolnym urządzeniu z systemem Windows 10. Aby to zrobić, możesz za pomocą szablonu projektu uniwersalnej platformy Windows (UWP), Extensible Application Markup Language (XAML), a C# języka programowania.

::: moniker range="vs-2017"
Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.
::: moniker-end
::: moniker range="vs-2019"
Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) strony, aby zainstalować go za darmo.
::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt Universal Windows Platform. Typ projektu jest dostarczany z wszystkie pliki szablonu, czego potrzebujesz, zanim dodaniu jeszcze nic!

1. Otwórz program Visual Studio.

::: moniker range="vs-2017"

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **Visual C#** , a następnie wybierz **Windows Universal**. W środkowym okienku wybierz **pusta aplikacja (Windows Universal)**. Następnie nadaj projektowi nazwę *HelloWorld* i wybierz polecenie **OK**.

   ![Windows Universal szablonu projektu w oknie dialogowym Nowy projekt w środowisku IDE programu Visual Studio](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Jeśli nie widzisz **pusta aplikacja (Windows Universal)** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe.<br><br>![Kliknij link Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Uruchamia Instalatora programu Visual Studio. Wybierz **programowania na platformę uniwersalną Windows** obciążenia, a następnie wybierz **Modyfikuj**.<br><br>![Uniwersalne obciążenie projektowania platformy Windows w Instalatorze programu Visual Studio](media/uwp-dev-workload.png)

4. Zaakceptuj wartość domyślną **wersji docelowej** i **minimalna wersja** ustawienia w **nowy projekt platformy Windows Universal** okno dialogowe.

   ![Zaakceptuj domyślną wersję docelowej i minimalnej wersji ustawień w oknie dialogowym Nowy projekt platformy Universal Windows](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"

2. Otwórz program Visual Studio, a następnie w oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

3. Na **Utwórz nowy projekt** ekranu, należy wprowadzić *Universal Windows* w polu wyszukiwania, wybierz opcję C# szablon **pusta aplikacja (Windows Universal)**, a następnie wybierz pozycję **Dalej**.

   ![Zrzut ekranu przedstawiający tworzenie nowego ekranu projektu](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Jeśli nie widzisz **pusta aplikacja (Windows Universal)** szablonu projektu, kliknij przycisk **zainstalować więcej narzędzi i funkcji** łącza.<br><br>![Kliknij przycisk Instaluj, link więcej narzędzi i funkcji](media/vs-2019/uwp-not-finding.png)<br><br>Uruchamia Instalatora programu Visual Studio. Wybierz **programowania na platformę uniwersalną Windows** obciążenia, a następnie wybierz **Modyfikuj**.<br><br>![Uniwersalne obciążenie projektowania platformy Windows w Instalatorze programu Visual Studio](media/uwp-dev-workload.png)

4. Zaakceptuj wartość domyślną **wersji docelowej** i **minimalna wersja** ustawienia w **nowy projekt platformy Windows Universal** okno dialogowe.

   ![Zaakceptuj domyślną wersję docelowej i minimalnej wersji ustawień w oknie dialogowym Nowy projekt platformy Universal Windows](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Jeśli po raz pierwszy używasz programu Visual Studio do tworzenia aplikacji platformy uniwersalnej systemu Windows, **ustawienia** może zostać wyświetlone okno dialogowe. Wybierz **tryb dewelopera**, a następnie wybierz **tak**.<br><br>
   ![Włącz tryb dewelopera w oknie dialogowym Ustawienia platformy uniwersalnej systemu Windows](media/enable-developer-mode.png)<br><br>Program Visual Studio zainstaluje dodatkowego pakietu tryb dewelopera. Po zakończeniu instalacji pakietu aktualizacji Zamknij **ustawienia** okno dialogowe.

## <a name="create-the-application"></a>Tworzenie aplikacji

Nadszedł czas, aby rozpocząć tworzenie. Będzie Dodaj kontrolkę przycisk, Dodaj akcję do przycisku, a następnie uruchom aplikację "Hello World", aby zobaczyć, jak to wygląda.

### <a name="add-a-button-to-the-design-canvas"></a>Dodawanie przycisku do obszaru roboczego projektowania

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie *MainPage.xaml* można otworzyć widoku podzielonego.

   ::: moniker range="vs-2017"
   ![Otwórz plik MainPage.xaml z poziomu Eksploratora rozwiązań ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Otwórz plik MainPage.xaml z poziomu Eksploratora rozwiązań](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Istnieją dwa okienka: **Projektanta XAML**, która obejmuje kanwą i **edytora XAML**, którym można dodać lub zmienić kod.

   ![W okienku projektanta XAML w edytorze XAML](media/uwp-xaml-editor.png)

2. Wybierz **przybornika** można otworzyć okna wysuwanego przybornika.

   ![Kliknij przycisk przybornika, aby otworzyć okno staną się przybornika](media/uwp-toolbox.png)

   (Jeśli nie widzisz **przybornika** opcji, możesz go otworzyć z paska menu. Aby to zrobić, wybierz **widoku** > **narzędzi**. Lub naciśnij **Ctrl**+**Alt**+**X**.)

3. Kliknij przycisk **numeru Pin** ikonę, aby zadokować okno przybornika.

   ![Kliknij ikonę pinezki, aby zadokować okno przybornika](media/uwp-toolbox-autohide.png)

4. Kliknij przycisk **przycisk** sterowania, a następnie przeciągnij go do obszaru roboczego projektowania.

   ![Kliknij formant przycisku i przeciągnij je na kanwę projektu](media/uwp-toolbox-add-button-control.png)

   Jeśli spojrzysz na kod w **edytora XAML**, zobaczysz, że przycisk został dodany, za:

   ![Kliknij formant przycisku i przeciągnij je na kanwę projektu](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Dodaj etykietę do przycisku

1. W **edytora XAML**, zmień wartość przycisk zawartości z "Button" na "Hello World!"

   ![Zmień wartość zawartości przycisku na Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

2. Należy zauważyć, że przycisk w **projektanta XAML** zmienia zbyt.

   ![Przycisk zmienia się na aplikację Hello World na kanwę projektu](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Dodawanie obsługi zdarzeń

Skomplikowane dźwięki "program obsługi zdarzeń", ale jest po prostu inną nazwę dla kodu, która jest wywoływana w przypadku wystąpienia zdarzenia. W tym przypadku dodaje akcję "Hello World!" przycisk.

1. Kliknij dwukrotnie formant przycisku w obszarze roboczym projektu.

2. Edytuj kod obsługi zdarzeń w *MainPage.xaml.cs*, na stronie związanym z kodem.

   Jest to, skąd pobrać interesujących rzeczy. Domyślny program obsługi zdarzeń wygląda następująco:

   ![Domyślny program obsługi zdarzeń Button_Click ](media/uwp-button-click-code.png)

   Zmieńmy go tak, aby wyglądał następująco:

   ![Nowy program obsługi zdarzeń Button_Click async ](media/uwp-add-hello-world-async-code.png)

   Poniżej przedstawiono kod, aby skopiować i wkleić:

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

#### <a name="what-did-we-just-do"></a>Co to po prostu zrobiliśmy?

Kod używa niektóre interfejsy API Windows w celu utworzenia obiektu synteza mowy i nadaje jej po jakiś tekst powiedzieć. (Aby uzyskać więcej informacji na temat korzystania z `SpeechSynthesis`, zobacz <xref:System.Speech.Synthesis>.)

## <a name="run-the-application"></a>Uruchamianie aplikacji

Nadszedł czas na tworzenie, wdrażanie i uruchomić aplikację "Hello World" platformy uniwersalnej systemu Windows, aby zobaczyć, co wyglądu i dźwięki, np. Poniżej przedstawiono sposób.

1. Użyj przycisku odtwarzania (ma tekst **komputera lokalnego**) do uruchamiania aplikacji na komputerze lokalnym.

   ![Kliknij komputer lokalny, aby uruchomić i debugowanie aplikacji platformy uniwersalnej systemu Windows](media/uwp-start-or-debug.png)

   (Można też wybrać **debugowania** > **Rozpocznij debugowanie** z paska menu lub naciśnij klawisz F5, aby uruchomić aplikację.)

2. Wyświetl aplikację, która pojawia się, gdy ekran powitalny zniknie. Aplikacja powinna wyglądać mniej więcej tak:

   ![A UWP "Hello World" app](media/uwp-hello-world-app.png)

3. Kliknij przycisk **Witaj, świecie** przycisku.

   Usługi systemu Windows 10, urządzenie dosłownie wyświetli komunikat, "Hello, World!"

4. Aby zamknąć aplikację, kliknij przycisk **Zatrzymaj debugowanie** przycisku na pasku narzędzi. (Wybierz również **debugowania** > **Zatrzymaj debugowanie** z paska menu lub naciśnij klawisze Shift + F5.)

## <a name="next-steps"></a>Następne kroki

Gratulujemy wykonanie kroków tego samouczka! Mamy nadzieję, że znasz już pewne podstawowe informacje dotyczące platformy uniwersalnej systemu Windows i środowiska IDE programu Visual Studio. Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Tworzenie interfejsu użytkownika](/windows/uwp/design/basics/xaml-basics-ui)
