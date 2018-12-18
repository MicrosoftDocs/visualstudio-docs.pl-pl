---
title: Utwórz swoją pierwszą aplikację konsoli za pomocą Visual Basic
description: Dowiedz się, jak utworzyć prostą aplikację konsoli Hello World w programie Visual Studio za pomocą Visual Basic, który krok po kroku.
ms.date: 12/10/2017
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.technology: vs-acquisition
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 67a990b98b385cacab89bfa8270d8409f9e9aa5f
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159610"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Szybki Start: Utwórz swoją pierwszą aplikację konsoli w programie Visual Studio za pomocą Visual Basic

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut utworzysz prostą aplikację języka Visual Basic, która działa na konsoli.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku Visual Basic. Typ projektu jest dostarczany z wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic!

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **języka Visual Basic**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **Aplikacja konsoli (.NET Core)**. Nadaj projektowi nazwę *HelloWorld*.

   ![Szablon projektu aplikacji (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE konsoli](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe.

   ![Kliknij link Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

     ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

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
> [Wprowadzenie do języka Visual Basic w programie Visual Studio](tutorial-visual-basic-console.md)
