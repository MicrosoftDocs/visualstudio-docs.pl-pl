---
title: Tworzenie pierwszej aplikacji konsolowej przy użyciu Visual Basic
description: Dowiedz się, jak utworzyć prostą Hello world konsolową w Visual Studio, Visual Basic, krok po kroku.
ms.custom: acquisition, seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 7272e02ebfba084bdbe311d10b69d7b41fade0e1
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307911"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Szybki start: tworzenie pierwszej aplikacji konsolowej w Visual Studio za pomocą Visual Basic

W tym 5–10-minutowym wprowadzeniu do zintegrowanego środowiska projektowego (IDE) usługi Visual Studio utworzysz prostą aplikację Visual Basic, która działa w konsoli.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji Visual Basic aplikacji. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek do ciebie dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję Visual Basic , **a** następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj *projektowi nazwę HelloWorld*.

   ![Szablon projektu aplikacja konsolowa (.NET Core) w oknie dialogowym Nowy projekt w Visual Studio IDE](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz szablonu projektu Aplikacja konsoli **(.NET Core),** kliknij **link** Otwórz Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt.

   ![Kliknij link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie Tworzenie aplikacji dla wielu platform na platformie **.NET Core,** a następnie wybierz pozycję **Modyfikuj.**

     ![Międzyplatformowe obciążenie programowe platformy .NET Core w Instalator programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu w tym przewodniku Szybki start używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [Personalizowanie](quickstart-personalize-the-ide.md) środowiska IDE i edytora Visual Studio, aby dowiedzieć się, jak to zrobić.

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Tworzenie nowego projektu** wybierz pozycję **Visual Basic** z listy Język. Następnie wybierz pozycję **Windows** z listy Platforma i **pozycję Konsola** z listy typów projektów.

   Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **Aplikacja konsolowa,** a następnie wybierz pozycję **Dalej.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Wybieranie Visual Basic szablonu aplikacji konsolowej":::

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa,** możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie można znaleźć tego,** czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w chmurze Instalator programu Visual Studio obciążenie tworzenie aplikacji dla wielu platform na **platformie .NET Core.**
   >
   > ![Międzyplatformowe obciążenie programowe platformy .NET Core w Instalator programu Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Tworzenie projektu".](#create-a-project)

1. W **oknie Konfigurowanie nowego** projektu wpisz lub wprowadź *wartość WhatIsYourName* w **polu Nazwa** projektu. Następnie wybierz pozycję **Dalej.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png" alt-text="W oknie &quot;Konfigurowanie nowego projektu&quot; nadaj projektowi nazwę &quot;WhatIsYourName&quot;":::

1. W **oknie Dodatkowe informacje** dla struktury docelowej należy już wybrać platformę **.NET Core 3.1.** Jeśli nie, wybierz **pozycję .NET Core 3.1.** Następnie wybierz pozycję **Utwórz**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="W oknie &quot;Dodatkowe informacje&quot; upewnij się, że wybrano opcję .NET Core 3.1":::

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu Visual Basic projektu i nazwaniu projektu Visual Studio aplikację "Hello world". Wywołuje metodę <xref:System.Console.WriteLine%2A> , aby wyświetlić ciąg literału "Hello world!" w oknie konsoli.

![Wyświetlanie domyślnego Hello world kodu z szablonu](../ide/media/vb-console-helloworld-template.png)

Po kliknięciu przycisku **HelloWorld** w idee IDE możesz uruchomić program w trybie debugowania.

  ![Kliknij przycisk Hello world, aby uruchomić program w trybie debugowania](../ide/media/vb-console-hello-world-button.png)

Gdy to zrobisz, okno konsoli będzie widoczne tylko przez chwilę, zanim zostanie zamknięte. Dzieje się tak, ponieważ metoda kończy działanie po wykonaniu jej pojedynczej `Main` instrukcji, a więc aplikacja zostaje zakończona.

### <a name="add-some-code&quot;></a>Dodawanie kodu

Dodajmy kod w celu wstrzymania aplikacji, a następnie poproś o wprowadzenie danych przez użytkownika.

1. Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine%2A> metody :

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

    To wstrzymuje program do momentu naciśnięcia klawisza.

2. Na pasku menu wybierz pozycję Build Build Solution   >  **(Skompilowanie rozwiązania kompilacji).**

   To kompiluje program do języka pośredniego (IL), który jest konwertowany na kod binarny przez kompilator jit (just in time).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **HelloWorld** na pasku narzędzi.

   ![Kliknij przycisk Hello world, aby uruchomić program na pasku narzędzi](../ide/media/vb-console-hello-world-button.png)

2. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

   ![Okno konsoli z Hello world i naciśnij dowolny klawisz, aby kontynuować](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego przewodnika Szybki start! Mamy nadzieję, że wiesz już trochę o Visual Basic i Visual Studio IDE. Aby dowiedzieć się więcej, przejdź do następującego samouczka.

> [!div class="nextstepaction"]
> [Rozpoczynanie pracy z Visual Basic w Visual Studio](../get-started/visual-basic/tutorial-console.md)
