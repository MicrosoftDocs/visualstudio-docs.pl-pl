---
title: 'Samouczek: Debugowanie C# i kodu w języku C++ (tryb mieszany)'
description: Dowiedz się, jak można debugować natywną bibliotekę DLL z aplikacji platformy .NET Core lub .NET Framework za pomocą debugowania trybu mieszanego
ms.custom: seodec18
ms.date: 11/02/2018
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: a987904b099e9a463f33eb77980abd3fa2f32d16
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790319"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Samouczek: Debugowanie C# i C++ w tej samej sesji debugowania

Program Visual Studio pozwala włączyć więcej niż jeden typ debugera w sesji debugowania, która jest wywoływana, debugowanie w trybie mieszanym. W tym samouczku przedstawiono sposób debugowania kodu zarządzanego i natywnego w jednej sesji debugowania.

W tym samouczku pokazano, jak można debugować kodu natywnego z zarządzanej aplikacji, ale możesz też [debugować kodu zarządzanego z aplikacji natywnej](../debugger/how-to-debug-in-mixed-mode.md). Debuger obsługuje również debugowanie w trybie mieszanym, takich jak debugowanie innych typów [języka Python i kodu natywnego](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)i w typach aplikacji, takich jak ASP.NET przy użyciu debugera skryptów.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Tworzenie prostego natywnej biblioteki DLL
> * Utwórz prostą aplikację platformy .NET Core lub .NET Framework do wywoływania biblioteki DLL
> * Konfigurowanie debugowania trybu mieszanego
> * Uruchom debuger
> * Trafiony punkt przerwania w aplikacji zarządzanej
> * Wejdź do kodu natywnego

## <a name="prerequisites"></a>Wymagania wstępne

Konieczne jest posiadanie programu Visual Studio, z następującymi pakietami roboczymi:
- **Programowanie aplikacji klasycznych w języku C++**
- Albo **programowanie aplikacji klasycznych dla platformy .NET** lub **platformy .NET Core programowanie wieloplatformowych**, w zależności od typu aplikacji, którą chcesz utworzyć.

Jeśli nie masz programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

Jeśli zainstalowano program Visual Studio, ale nie ma obciążenia wybierz **Otwórz Instalator programu Visual Studio** w okienku po lewej stronie programu Visual Studio **nowy projekt** okno dialogowe. W Instalatorze programu Visual Studio, wybierz obciążenia potrzebujesz, a następnie wybierz **Modyfikuj**.

## <a name="create-a-simple-native-dll"></a>Tworzenie prostego natywnej biblioteki DLL

**Aby utworzyć pliki w projekcie biblioteki DLL:**

1. Otwórz program Visual Studio i Utwórz projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **Esc** aby zamknąć okno rozpoczęcia. Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **pusty projekt**, wybierz **szablony**, następnie wybierz **Utwórz nowy pusty projekt** dla języka C ++. W oknie dialogowym wybierz **Utwórz**. Następnie wpisz nazwę, takich jak **Mixed_Mode_Debugging** i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** dialogowego **Visual C++**, wybierz **innych**, a następnie w środkowym okienku wybierz **pusty projekt**. Następnie wpisz nazwę, takich jak **Mixed_Mode_Debugging** i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz **pusty projekt** szablon projektu, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...** , która otwiera Instalatora programu Visual Studio. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych w języku C++** obciążenia, wybierz **Modyfikuj**.

    Program Visual Studio tworzy projekt.

1. W **nowy projekt** dialogowego **Visual C++**, wybierz opcję **innych**, a następnie wybierz pozycję **pusty projekt** w środkowym okienku.

1. W **nazwa** wpisz **Mixed_Mode_Debugging**, a następnie wybierz pozycję **OK**.

   Tworzy pusty projekt programu Visual Studio i wyświetla go w **Eksploratora rozwiązań**.

1. W **Eksploratora rozwiązań**, wybierz opcję **pliki źródłowe**, a następnie wybierz pozycję **projektu** > **Dodaj nowy element**. Lub kliknij prawym przyciskiem myszy **pliki źródłowe** i wybierz **Dodaj** > **nowy element**.

1. W **nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)**. Typ **Mixed_Mode.cpp** w **nazwa** , a następnie wybierz opcję **Dodaj**.

    Program Visual Studio dodaje nowy plik C++ **Eksploratora rozwiązań**.

1. Skopiuj następujący kod do *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. W **Eksploratora rozwiązań**, wybierz opcję **pliki nagłówkowe**, a następnie wybierz pozycję **projektu** > **Dodaj nowy element**. Lub kliknij prawym przyciskiem myszy **pliki nagłówkowe** i wybierz **Dodaj** > **nowy element**.

1. W **nowy element** okno dialogowe, wybierz opcję **plik nagłówka (.h)**. Typ **Mixed_Mode.h** w **nazwa** , a następnie wybierz opcję **Dodaj**.

   Program Visual Studio dodaje nowy plik nagłówkowy do **Eksploratora rozwiązań**.

1. Skopiuj następujący kod do *Mixed_Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
      __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
        return a * b;
      }
    }
    #endif
    ```

1. Wybierz **pliku** > **Zapisz wszystko** lub naciśnij **Ctrl**+**Shift**+**S**  do zapisania plików.

**Aby skonfigurować i skompiluj projekt DLL:**

1. Na pasku narzędzi programu Visual Studio wybierz **debugowania** konfiguracji i **x86** lub **x64** platformy. Jeśli wywołujący aplikacja nie będzie platformy .NET Core, która zawsze działa w trybie 64-bitowym, wybierz pozycję **x64** jako platformę.

1. W **Eksploratora rozwiązań**, wybierz opcję **Mixed_Mode_Debugging** węzeł projektu i wybierz pozycję **właściwości** ikonę, lub kliknij prawym przyciskiem myszy węzeł projektu i wybierz pozycję **Właściwości**.

1. W górnej części **właściwości** okienka, upewnij się, że **konfiguracji** jest ustawiona na **Active(Debug)** i **platformy** jest taka sama jak tym, co Ustaw na pasku narzędzi: **x64**, lub **Win32** dla x86 platformy.

   > [!IMPORTANT]
   > Po przełączeniu Platforma **x86** do **x64** lub na odwrót, należy ponownie skonfigurować właściwości dla nowej platformie.

1. W obszarze **właściwości konfiguracji** w okienku po lewej stronie wybierz **konsolidatora** > **zaawansowane**i w menu rozwijanym obok **punkt wejścia nie**, wybierz opcję **nie**. Jeśli konieczna była zmiana jego **nie**, wybierz opcję **Zastosuj**.

1. W obszarze **właściwości konfiguracji**, wybierz opcję **ogólne**i w menu rozwijanym obok **typu konfiguracji**, wybierz opcję **Biblioteka dynamiczna (dll)**. Wybierz **Zastosuj**, a następnie wybierz pozycję **OK**.

   ![Przełącz się do macierzystych bibliotek DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Wybierz projekt w **Eksploratora rozwiązań** , a następnie wybierz **kompilacji** > **Kompiluj rozwiązanie**, naciśnij klawisz **F7**, lub kliknij prawym przyciskiem myszy Projekt i wybierz pozycję **kompilacji**.

   Projekt powinien być kompilowany bez błędów.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Tworzenie prostej aplikacji zarządzanych do wywoływania biblioteki DLL

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **Esc** aby zamknąć okno rozpoczęcia. Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **konsoli**, wybierz **szablony**, a następnie wybierz **Utwórz nowy projekt aplikacji konsoli (.NET Framework)** dla C#. W oknie dialogowym wybierz **Utwórz**.

    Następnie wpisz nazwę, takich jak **Mixed_Mode_Calling_App** i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okno dialogowe, w obszarze **Visual C#** , wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **Aplikacja konsoli (. Program .NET Framework)** lub **konsoli aplikacji (.NET Core)**.

    Następnie wpisz nazwę, takich jak **Mixed_Mode_Calling_App** i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz **aplikacja Konsolowa** szablon projektu, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...** , która otwiera Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, wybierz **Modyfikuj**.

    > [!NOTE]
    > Mimo, że nowy projekt zarządzanych można również dodać do istniejącego rozwiązania do języka C++, tworząc nowe rozwiązanie obsługuje więcej scenariuszy debugowania.

   Tworzy pusty projekt programu Visual Studio i wyświetla go w **Eksploratora rozwiązań**.

1. Zastąp cały kod w *Program.cs* następującym kodem:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. W nowym kodzie Zastąp ścieżki pliku w `[DllImport]` swoją ścieżką pliku do *Mixed_Mode_Debugging.dll* właśnie utworzony. Zobacz komentarz kod dla wskazówek dotyczących serwerów. Upewnij się zastąpić *username* symbol zastępczy.

1. Wybierz **pliku** > **Zapisz plik Program.cs** lub naciśnij **Ctrl**+**S** można zapisać pliku.

## <a name="configure-mixed-mode-debugging"></a>Konfigurowanie debugowania trybu mieszanego

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Aby skonfigurować dla aplikacji programu .NET Framework debugowanie w trybie mieszanym

1. W **Eksploratora rozwiązań**, wybierz opcję **Mixed_Mode_Calling_App** węzeł projektu i wybierz pozycję **właściwości** ikonę, lub kliknij prawym przyciskiem myszy węzeł projektu i wybierz pozycję **Właściwości**.

1. Wybierz **debugowania** w okienku po lewej stronie wybierz **Włącz debugowanie kodu natywnego** pole wyboru, a następnie zamknij stronę właściwości, aby zapisać zmiany.

    ![Włącz debugowanie w trybie mieszanym](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Aby skonfigurować debugowanie w trybie mieszanym dla aplikacji platformy .NET Core

W większości wersji programu Visual Studio 2017, musisz użyć *launchSettings.json* pliku zamiast właściwości projektu, aby włączyć debugowanie w trybie mieszanym dla kodu natywnego w aplikacji platformy .NET Core. Aby śledzić aktualizacje interfejsu użytkownika dla tej funkcji, zobacz ten [problem w usłudze GitHub](https://github.com/dotnet/project-system/issues/1125).

1. W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości**, a następnie otwórz *launchSettings.json* pliku.

   >[!NOTE]
   >Domyślnie *launchSettings.json* znajduje się w *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Jeśli *launchSettings.json* nie istnieje, wybierz **Mixed_Mode_Calling_App** projektu w **Eksploratora rozwiązań** , a następnie wybierz **właściwości** ikonę, lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**. Tymczasowe zmiany w **debugowania** kartę i skompiluj projekt. Spowoduje to utworzenie *launchSettings.json* pliku. Cofnąć zmiany wprowadzone w **debugowania** kartę.

1. W *lauchsettings.json* plików, Dodaj następujący wiersz:

    ```csharp
    "nativeDebugging": true
    ```

    Kompletny plik będzie wyglądać następująco:

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-debugging"></a>Ustaw punkt przerwania, a następnie rozpocząć debugowanie

1. W C# otwarty projekt *Program.cs*. Ustaw punkt przerwania na następujący wiersz kodu, klikając na lewym marginesie, zaznaczając wiersz i naciskając klawisz **F9**, lub kliknij prawym przyciskiem myszy wiersza i wybierając **punktu przerwania**  >  **Wstaw punkt przerwania**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Czerwony okrąg pojawia się na lewym marginesie, gdzie ustawić punkt przerwania.

1. Naciśnij klawisz **F5**, wybierz zieloną strzałkę na pasku narzędzi programu Visual Studio, lub **debugowania** > **Rozpocznij debugowanie** można rozpocząć debugowania.

   Debuger zatrzymuje się na punkcie przerwania, który został ustawiony. Żółta strzałka wskazuje, gdzie debuger jest obecnie wstrzymana.

## <a name="step-in-and-out-of-native-code"></a>Krok i z kodu natywnego

1. Podczas debugowania jest wstrzymana w aplikacji zarządzanej, naciśnij klawisz **F11**, lub wybierz **debugowania** > **Step Into**.

   *Mixed_Mode.h* otwiera plik nagłówkowy natywnych i zostanie wyświetlona żółta strzałka, gdy debuger jest wstrzymana.

   ![Wejdź do kodu natywnego](../debugger/media/mixed-mode-step-into-native-code.png)

1. Teraz można ustawić i identyfikować punkty przerwania i sprawdzanie zmiennych w kodzie macierzystym lub zarządzane.

   - Umieść kursor nad zmiennych w kodzie źródłowym, aby zobaczyć ich wartości.

   - Przyjrzyj się zmienną i ich wartości w **Autos** i **lokalne** systemu windows.

   - Wstrzymaniu w debugerze, ale można również używać **Obejrzyj** systemu windows i **stos wywołań** okna.

1. Naciśnij klawisz **F11** ponownie w celu przechodzenia debugera jeden wiersz.

1. Naciśnij klawisz **Shift**+**F11** lub wybierz **debugowania** > **Step Out** chcesz kontynuować wykonywanie i wstrzymać ponownie w Aplikacja zarządzana.

1. Naciśnij klawisz **F5** lub wybierz zieloną strzałkę, aby kontynuować debugowanie aplikacji.

Gratulacje! Ukończono samouczek na temat debugowania trybu mieszanego.

## <a name="next-step"></a>Następny krok

W tym samouczku przedstawiono sposób debugowania kodu macierzystego z zarządzanej aplikacji, należy włączyć debugowanie w trybie mieszanym. Aby uzyskać przegląd innych funkcji debugera zobacz:

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
