---
title: 'Samouczek: Debugowanie kodu C# i C++ (tryb mieszany)'
description: Dowiedz się, jak debugować natywną bibliotekę DLL z aplikacji .NET Core lub .NET Framework przy użyciu debugowania w trybie mieszanym
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
ms.openlocfilehash: 06f68962eb7cdb6e4fc0290ee5c6559721afb52b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77416363"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Samouczek: Debugowanie C# i C++ w tej samej sesji debugowania

Visual Studio umożliwia włączenie więcej niż jednego typu debugera w sesji debugowania, który jest nazywany debugowania w trybie mieszanym. W tym samouczku nauczysz się debugować kod zarządzany i natywny w jednej sesji debugowania.

W tym samouczku pokazano, jak debugować kod macierzysty z zarządzanej aplikacji, ale można również [debugować kod zarządzany z aplikacji macierzystej](../debugger/how-to-debug-in-mixed-mode.md). Debuger obsługuje również inne typy debugowania w trybie mieszanym, takie jak debugowanie [języka Python i kod macierzysty](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md), i przy użyciu debugera skryptów w typach aplikacji, takich jak ASP.NET.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Tworzenie prostej macierzystej biblioteki DLL
> * Tworzenie prostej aplikacji .NET Core lub .NET Framework w celu wywołania biblioteki DLL
> * Konfigurowanie debugowania w trybie mieszanym
> * Uruchamianie debugera
> * Trafienie punktu przerwania w zarządzanej aplikacji
> * Krok do kodu macierzystego

## <a name="prerequisites"></a>Wymagania wstępne

Program Visual Studio musi być zainstalowany z następującymi obciążeniami:
- **Tworzenie komputerów stacjonarnych w języku C++**
- **Programowy pulpitu platformy .NET** lub **program .NET Core —** w zależności od typu aplikacji, którą chcesz utworzyć.

Jeśli nie masz programu Visual Studio, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.

Jeśli masz zainstalowany program Visual Studio, ale nie masz potrzebnych obciążeń, wybierz **otwórz Instalatora programu Visual Studio** w lewym okienku okna dialogowego Visual Studio New **Project.** W Instalatorze programu Visual Studio wybierz potrzebne obciążenia, a następnie wybierz pozycję **Modyfikuj**.

## <a name="create-a-simple-native-dll"></a>Tworzenie prostej macierzystej biblioteki DLL

**Aby utworzyć pliki dla projektu biblioteki DLL:**

1. Otwórz program Visual Studio i utwórz projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **Pusty projekt**, wybierz pozycję **Szablony,** a następnie wybierz pozycję Pusty **projekt** dla języka C++. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**. Następnie wpisz nazwę, taką jak **Mixed_Mode_Debugging** i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C++** wybierz pozycję **Inne**, a następnie w środkowym okienku wybierz pozycję **Pusty projekt**. Następnie wpisz nazwę, taką jak **Mixed_Mode_Debugging** i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **Pusty projekt,** przejdź do **narzędzia Pobierz** > **narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Uruchamia instalator programu Visual Studio. Wybierz program rozwoju pulpitu z obciążeniem **języka C++,** a następnie wybierz pozycję **Modyfikuj**.

    Visual Studio tworzy projekt.

1. W **Eksploratorze rozwiązań**wybierz pozycję **Pliki źródłowe**, a następnie wybierz pozycję **Project** > **Add New Item**. Możesz też kliknąć prawym przyciskiem myszy **pozycję Pliki źródłowe** i wybrać pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Nowy element** wybierz **plik C++ (cpp)**. Wpisz **Mixed_Mode.cpp** w polu **Nazwa,** a następnie wybierz pozycję **Dodaj**.

    Program Visual Studio dodaje nowy plik C++ do **Eksploratora rozwiązań**.

1. Skopiuj następujący kod do *Mixed_Mode.cpp:*

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. W **Eksploratorze rozwiązań**wybierz pozycję **Pliki nagłówkowe**, a następnie wybierz pozycję **Project** > **Add New Item**. Możesz też kliknąć prawym przyciskiem myszy **pozycję Pliki nagłówkowe** i wybrać pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Nowy element** wybierz pozycję **Plik nagłówka (h)**. Wpisz **Mixed_Mode.h** w polu **Nazwa,** a następnie wybierz pozycję **Dodaj**.

   Program Visual Studio dodaje nowy plik nagłówka do **Eksploratora rozwiązań**.

1. Skopiuj poniższy kod do *Mixed_Mode.h:*

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

1. Wybierz **pozycję Zapisz** > **wszystkie** pliki lub naciśnij klawisz **Ctrl**+**Shift**+**S,** aby zapisać pliki.

**Aby skonfigurować i utworzyć projekt biblioteki DLL:**

1. Na pasku narzędzi Programu Visual Studio wybierz opcję Konfiguracja **debugowania** i platforma **x86** lub **x64.** Jeśli aplikacja wywołująca będzie .NET Core, który zawsze działa w trybie 64-bitowym, wybierz **x64** jako platformę.

1. W **Eksploratorze rozwiązań**wybierz **węzeł projektu Mixed_Mode_Debugging** i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.

1. U góry okienka **Właściwości** upewnij się, że konfiguracja jest **ustawiona** na **Active(Debug),** a **platforma** jest taka sama, jak ustawiona na pasku narzędzi: **x64**lub **Win32** dla platformy x86.

   > [!IMPORTANT]
   > Jeśli przełączysz platformę z **x86** na **x64** lub odwrotnie, należy ponownie skonfigurować właściwości dla nowej platformy.

1. W obszarze **Właściwości konfiguracji** w lewym okienku wybierz pozycję **Linker** > **Advanced**, a następnie w menu rozwijanym obok pozycji Brak **punktu wejścia**wybierz pozycję **Nie**. Jeśli trzeba było zmienić go na **Nie,** wybierz opcję **Zastosuj**.

1. W obszarze **Właściwości konfiguracji**wybierz pozycję **Ogólne**, a na menu obok pozycji **Typ konfiguracji**wybierz pozycję **Biblioteka dynamiczna (dll).** Wybierz pozycję **Apply** (Zastosuj), a następnie wybierz przycisk **OK**.

   ![Przełączanie na macierzystą bibliotekę DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Wybierz projekt w **Eksploratorze rozwiązań,** a następnie wybierz pozycję **Zbuduj** > **rozwiązanie kompilacji**, naciśnij **klawisz F7**lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Kompilacja**.

   Projekt powinien być kompilowany bez błędów.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Tworzenie prostej zarządzanej aplikacji do wywoływania biblioteki DLL

1. Otwórz program Visual Studio i utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **klawisze Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **konsolę**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** lub Aplikacja konsoli **(.NET Framework)** dla języka C#. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.

    Następnie wpisz nazwę, taką jak **Mixed_Mode_Calling_App** i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C#** wybierz pozycję **Pulpit systemu Windows**, a następnie w środkowym okienku wybierz pozycję Aplikacja **konsoli (.NET Framework)** lub **Aplikacja konsoli (.NET Core).**

    Następnie wpisz nazwę, taką jak **Mixed_Mode_Calling_App** i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **aplikacji konsoli,** przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Wybierz obciążenie **programistyczne dla komputerów .NET,** a następnie wybierz pozycję **Modyfikuj**.

    > [!NOTE]
    > Chociaż można również dodać nowy projekt zarządzany do istniejącego rozwiązania Języka C++, tworzenie nowego rozwiązania obsługuje więcej scenariuszy debugowania.

   Program Visual Studio tworzy pusty projekt i wyświetla go w **Eksploratorze rozwiązań**.

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

1. W nowym kodzie zastąp ścieżkę pliku `[DllImport]` ścieżką pliku do *Mixed_Mode_Debugging.dll, który* właśnie utworzyłeś. Zobacz komentarz do kodu, aby uzyskać wskazówki. Pamiętaj, aby zastąpić symbol zastępczy *nazwy użytkownika.*

1. Wybierz **opcję** > Zapisz plik**Program.cs** lub naciśnij klawisz **Ctrl**+**S,** aby zapisać plik.

## <a name="configure-mixed-mode-debugging"></a>Konfigurowanie debugowania w trybie mieszanym

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Aby skonfigurować debugowanie w trybie mieszanym dla aplikacji .NET Framework

1. W **Eksploratorze rozwiązań**wybierz **węzeł projektu Mixed_Mode_Calling_App** i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.

1. Wybierz **pozycję Debugowanie** w lewym okienku, zaznacz pole wyboru **Włącz debugowanie kodu macierzystego,** a następnie zamknij stronę właściwości, aby zapisać zmiany.

    ![Włączanie debugowania w trybie mieszanym](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Aby skonfigurować debugowanie w trybie mieszanym dla aplikacji .NET Core

W większości wersji programu Visual Studio, począwszy od programu Visual Studio 2017, należy użyć pliku *launchSettings.json* zamiast właściwości projektu, aby włączyć debugowanie w trybie mieszanym dla kodu macierzystego w aplikacji .NET Core. Aby śledzić aktualizacje interfejsu użytkownika dla tej funkcji, zobacz ten [problem z usługą GitHub](https://github.com/dotnet/project-system/issues/1125).

1. W **Eksploratorze rozwiązań**rozwiń węzeł **Właściwości**i otwórz plik *launchSettings.json.*

   >[!NOTE]
   >Domyślnie *plik launchSettings.json* jest w *języku C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Jeśli *plik launchSettings.json* nie istnieje, wybierz **projekt Mixed_Mode_Calling_App** w **Eksploratorze rozwiązań,** a następnie wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. Wprowadzać tymczasowe zmiany na karcie **Debugowanie** i utworzyć projekt. Spowoduje to utworzenie pliku *launchSettings.json.* Przywróć zmianę wniesienia zmiany na karcie **Debugowanie.**

1. W pliku *launchsettings.json* dodaj następujący wiersz:

    ```csharp
    "nativeDebugging": true
    ```

    Kompletny plik będzie wyglądał następująco:

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

## <a name="set-a-breakpoint-and-start-debugging"></a>Ustawianie punktu przerwania i rozpoczynanie debugowania

1. W projekcie C# otwórz *Program.cs*. Ustaw punkt przerwania w następującym wierszu kodu, klikając na lewym marginesie, zaznaczając linię i naciskając **klawisz F9**lub klikając wiersz prawym przyciskiem myszy i wybierając punkt **przerwania** > **Insert Breakpoint**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Na lewym marginesie pojawi się czerwone kółko, na którym ustawiono punkt przerwania.

1. Naciśnij **klawisz F5**, wybierz zieloną strzałkę na pasku narzędzi Visual Studio lub wybierz pozycję **Debugowanie** > **rozpocznij debugowanie,** aby rozpocząć debugowanie.

   Debuger wstrzymuje punkt przerwania, który można ustawić. Żółta strzałka wskazuje, gdzie debuger jest obecnie wstrzymany.

## <a name="step-in-and-out-of-native-code"></a>Krok do kodu macierzystego i z nich

1. Podczas debugowania jest wstrzymany w aplikacji zarządzanej, naciśnij **klawisz F11**lub wybierz **debugowanie** > **step into**.

   Zostanie otwarty natywny plik nagłówka *Mixed_Mode.h,* a zostanie wyświetlona żółta strzałka, w której debuger jest wstrzymany.

   ![Krok do kodu macierzystego](../debugger/media/mixed-mode-step-into-native-code.png)

1. Teraz można ustawić i trafić punkty przerwania i sprawdzić zmienne w kodzie macierzystym lub zarządzanym.

   - Umieść wskaźnik myszy na zmiennych w kodzie źródłowym, aby wyświetlić ich wartości.

   - Spójrz na zmienną i ich wartości w **oknach Autos** i **Locals.**

   - Wstrzymane w debugerze można również użyć **okna czujki** i **stosu wywołań.**

1. Naciśnij ponownie **klawisz F11,** aby przejść do debugera o jedną linię.

1. Naciśnij **klawisz Shift**+**F11** lub wybierz pozycję**Wyjdź z** **debugowania,** > aby kontynuować wykonywanie i ponownie wstrzymać działanie w zarządzanej aplikacji.

1. Naciśnij **klawisz F5** lub wybierz zieloną strzałkę, aby kontynuować debugowanie aplikacji.

Gratulacje! Ukończono samouczek debugowania w trybie mieszanym.

## <a name="next-step"></a>Następny krok

W tym samouczku dowiesz się, jak debugować kod macierzysty z zarządzanej aplikacji, włączając debugowanie w trybie mieszanym. Aby uzyskać omówienie innych funkcji debugera, zobacz:

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
