---
title: Tworzenie pierwszej przy użyciu programu Visual Studio C# aplikacji konsoli
titleSuffix: ''
description: Dowiedz się, jak utworzyć prostą aplikację konsoli Hello World w programie Visual Studio w języku C#, krok po kroku.
ms.date: 09/21/2018
ms.custom: seodec18
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 12a08aa0e7509d04b522b74362347bc996e02946
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923737"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Szybki start: Tworzenie pierwszej przy użyciu programu Visual Studio C# aplikacji konsoli

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut utworzysz prostą C# aplikację, która działa na konsoli.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji C#. Typ projektu jest dostarczany z wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic!

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **C#**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **Aplikacja konsoli (.NET Core)**. Nadaj projektowi nazwę *HelloWorld*.

   ![Szablon projektu aplikacji (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE konsoli](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** projektu szablonu, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe.

   ![Wybierz łącze Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

     ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu C# i nazwij swój projekt, Visual Studio tworzy prostą aplikację "Hello World".

(Aby to zrobić, wywoływanych przez nią <xref:System.Console.WriteLine%2A> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli.)

   ![Wyświetlanie kodu Hello World domyślne z szablonu](../ide/media/csharp-console-helloworld-template.png)

Jeśli użytkownik naciśnie klawisz **F5**, program można uruchomić w trybie debugowania. Jednak okno konsoli jest widoczna tylko w przypadku chwilę przed jej zamknięciem.

(Zdarza się to `Main` metoda kończy się po wykonaniu jej pojedynczej instrukcji, więc kończy się aplikacja.)

### <a name="add-some-code"></a>Dodawanie kodu

Dodajmy trochę kodu, aby zatrzymać aplikację, tak aby nie zamyka okna konsoli, dopóki nie zostanie naciśnięty klawisz **ENTER**.

1. Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine%2A> metody:

   ```csharp
   Console.ReadLine();
   ```

1. Sprawdź, czy wygląda to w edytorze kodu:

   ![Dodaj kod, aby wstrzymać aplikacji Hello World](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz **HelloWorld** przycisk na pasku narzędzi, aby uruchomić aplikację w trybie debugowania. (Lub, możesz nacisnąć przycisk **F5**.)

   ![Wybierz przycisk Witaj, świecie, aby uruchomić aplikację z paska narzędzi](../ide/media/csharp-console-hello-world-button.png)

1. Wyświetlanie aplikacji w oknie konsoli.

   ![Okno konsoli przedstawiający Witaj, świecie!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Zamknij aplikację

1. Naciśnij klawisz **ENTER** aby zamknąć okno konsoli.

1. Zamknij **dane wyjściowe** okienko w programie Visual Studio.

   ![Zamknij okienko danych wyjściowych w programie Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Zamknij program Visual Studio.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco C# i środowisku IDE programu Visual Studio. Aby dowiedzieć się więcej, przejdź do następujących samouczków.

> [!div class="nextstepaction"]
> [Wprowadzenie do aplikacji konsolowej C# w programie Visual Studio](../get-started/csharp/tutorial-console.md)
