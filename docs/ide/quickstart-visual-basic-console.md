---
title: Utwórz swoją pierwszą aplikację konsoli za pomocą Visual Basic
description: Dowiedz się, jak utworzyć prostą aplikację konsoli Hello World w programie Visual Studio za pomocą Visual Basic, który krok po kroku.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 2ecfba0dceb7e7695a077464151e50f4dc042526
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650290"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Szybki start: Utwórz swoją pierwszą aplikację konsoli w programie Visual Studio za pomocą Visual Basic

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut utworzysz prostą aplikację języka Visual Basic, która działa na konsoli.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) strony, aby zainstalować go za darmo.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku Visual Basic. Typ projektu jest dostarczany z wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **języka Visual Basic**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **Aplikacja konsoli (.NET Core)**. Nadaj projektowi nazwę *HelloWorld*.

   ![Szablon projektu aplikacji (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE konsoli](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe.

   ![Kliknij link Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

     ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu, w tym przewodniku Szybki Start Użyj ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

1. Open Visual Studio 2019.

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

   ![Wyświetlanie w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na **Utwórz nowy projekt** oknie wprowadź lub wpisz *konsoli* w polu wyszukiwania. Następnie wybierz pozycję **języka Visual Basic** od języka, a następnie wybierz **Windows** z listy Platform. 

   Po zastosowaniu filtrów języka i platformy, wybierz **Aplikacja konsoli (.NET Core)** szablonu, a następnie wybierz **dalej**.

   ![Wybierz szablon języka Visual Basic dla aplikacji konsoli (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** szablonu, można zainstalować go z **Utwórz nowy projekt** okna. W **nie znaleźć, czego szukasz?** komunikatu, wybierz polecenie **zainstalować więcej narzędzi i funkcji** łącza.
   >
   > ![Łącza "Zainstaluj więcej narzędzi i funkcji" komunikat "Nie możesz znaleźć teraz wyszukiwanie" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalatorze programu Visual Studio, wybierz **programowanie dla wielu platform .NET Core** obciążenia.
   >
   > ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie należy wybrać **Modyfikuj** przycisku w Instalatorze programu Visual Studio. Może zostać wyświetlony monit, aby zapisać swoją pracę; Jeśli tak, należy to zrobić. Następnie wybierz pozycję **Kontynuuj** do zainstalowania z obciążeniem. Następnie wróć do kroku 2, w tym "[Utwórz projekt](#create-a-project)" procedury.

1. W **konfigurowania nowego projektu** oknie wpisz lub wprowadź *WhatIsYourName* w **Nazwa projektu** pole. Następnie wybierz **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" nazwij swój projekt "WhatIsYourName"](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu języka Visual Basic i nazwij swój projekt, Visual Studio tworzy prostą aplikację "Hello World". Wywołuje <xref:System.Console.WriteLine%2A> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli.

![Wyświetlanie kodu Hello World domyślne z szablonu](../ide/media/vb-console-helloworld-template.png)

Jeśli klikniesz **HelloWorld** przycisku w IDE, możesz uruchomić program w trybie debugowania.

  ![Kliknij przycisk Witaj, świecie, aby uruchomić program w trybie debugowania](../ide/media/vb-console-hello-world-button.png)

Gdy to zrobisz, okno konsoli jest widoczna na tylko chwilę przed jej zamknięciem. Wynika to z faktu `Main` metoda kończy się po wykonaniu jej pojedynczej instrukcji, więc kończy się w aplikacji.

### <a name="add-some-code"></a>Dodawanie kodu

Dodajmy trochę kodu, aby zatrzymać aplikację, a następnie poproś na dane wejściowe użytkownika.

1. Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine%2A> metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Wstrzymuje program, dopóki naciśnięciu przypisanego klawisza.

2. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

   Program to kompilowany na język pośredni (IL), który jest konwertowany na kod binarny przez kompilator just-in-time (JIT).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **HelloWorld** przycisk na pasku narzędzi.

   ![Kliknij przycisk Witaj, świecie, aby uruchomić program z paska narzędzi](../ide/media/vb-console-hello-world-button.png)

2. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

   ![Wyświetlanie Hello World w oknie konsoli, a następnie naciśnij dowolny klawisz, aby kontynuować](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco Visual Basic i Visual Studio IDE. Aby dowiedzieć się więcej, przejdź do następującego samouczka.

> [!div class="nextstepaction"]
> [Wprowadzenie do języka Visual Basic w programie Visual Studio](../get-started/visual-basic/tutorial-console.md)
