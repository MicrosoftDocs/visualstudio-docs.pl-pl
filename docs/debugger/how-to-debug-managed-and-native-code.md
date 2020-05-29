---
title: 'Samouczek: Debugowanie kodu C# i C++ (tryb mieszany)'
description: Dowiedz się, jak debugować natywną bibliotekę DLL z poziomu aplikacji .NET Core lub .NET Framework przy użyciu debugowania w trybie mieszanym
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
ms.openlocfilehash: 9f3fd94f8c294dce81bc69011e7d6f5fdd505325
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182641"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Samouczek: debugowanie C# i C++ w tej samej sesji debugowania

Program Visual Studio umożliwia włączenie więcej niż jednego typu debugera w sesji debugowania, która jest nazywana debugowaniem w trybie mieszanym. W ramach tego samouczka nauczysz się debugować kod zarządzany i natywny w pojedynczej sesji debugowania.

W tym samouczku pokazano, jak debugować kod natywny z zarządzanej aplikacji, ale można też [debugować kod zarządzany z aplikacji natywnej](../debugger/how-to-debug-in-mixed-mode.md). Debuger obsługuje również inne typy debugowania w trybie mieszanym, takie jak debugowanie [kodu Python i kod natywny](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)oraz korzystanie z debugera skryptów w typach aplikacji, takich jak ASP.NET.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Tworzenie prostej natywnej biblioteki DLL
> * Utwórz prostą aplikację platformy .NET Core lub .NET Framework, aby wywołać bibliotekę DLL
> * Konfigurowanie debugowania w trybie mieszanym
> * Uruchom Debuger
> * Trafienie punktu przerwania w zarządzanej aplikacji
> * Wkrocz do kodu natywnego

## <a name="prerequisites"></a>Wymagania wstępne

Musisz mieć zainstalowany program Visual Studio z następującymi obciążeniami:
- **Programowanie aplikacji klasycznych w języku C++**
- Programowanie aplikacji **klasycznych platformy .NET** lub platformę **.NET Core**, w zależności od tego, jakiego typu aplikacja ma zostać utworzona.

Jeśli nie masz programu Visual Studio, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.

Jeśli masz zainstalowany program Visual Studio, ale nie masz potrzebnych obciążeń, wybierz pozycję **otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** programu Visual Studio. W Instalator programu Visual Studio Wybierz potrzebne obciążenia, a następnie wybierz pozycję **Modyfikuj**.

## <a name="create-a-simple-native-dll"></a>Tworzenie prostej natywnej biblioteki DLL

**Aby utworzyć pliki dla projektu DLL:**

1. Otwórz program Visual Studio i Utwórz projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, **wpisz pusty projekt**, wybierz pozycję **Szablony**, a następnie wybierz **pusty projekt** dla języka C++. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**. Następnie wpisz nazwę, taką jak **Mixed_Mode_Debugging** , i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C++** wybierz pozycję **inne**, a następnie w środkowym okienku wybierz pozycję **pusty projekt**. Następnie wpisz nazwę, taką jak **Mixed_Mode_Debugging** , i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli szablon projektu **pusty projekt** nie jest widoczny, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz pozycję **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz polecenie **Modyfikuj**.

    Program Visual Studio tworzy projekt.

1. W **Eksplorator rozwiązań**wybierz pozycję **pliki źródłowe**, a następnie wybierz pozycję **projekt**  >  **Dodaj nowy element**. Lub kliknij prawym przyciskiem myszy pozycję **pliki źródłowe** i wybierz polecenie **Dodaj**  >  **nowy element**.

1. W oknie dialogowym **nowy element** wybierz pozycję **plik C++ (. cpp)**. Wpisz **Mixed_Mode. cpp** w polu **Nazwa** , a następnie wybierz pozycję **Dodaj**.

    Program Visual Studio dodaje nowy plik C++ do **Eksplorator rozwiązań**.

1. Skopiuj następujący kod do *Mixed_Mode. cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. W **Eksplorator rozwiązań**wybierz pozycję **pliki nagłówkowe**, a następnie wybierz pozycję **projekt**  >  **Dodaj nowy element**. Lub kliknij prawym przyciskiem myszy pozycję **pliki nagłówkowe** i wybierz polecenie **Dodaj**  >  **nowy element**.

1. W oknie dialogowym **nowy element** wybierz pozycję **plik nagłówka (. h)**. Wpisz **Mixed_Mode. h** w polu **Nazwa** , a następnie wybierz pozycję **Dodaj**.

   Program Visual Studio dodaje nowy plik nagłówka do **Eksplorator rozwiązań**.

1. Skopiuj następujący kod do *Mixed_Mode. h*:

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

1. Wybierz pozycję **plik**  >  **Zapisz wszystko** lub naciśnij klawisz **Ctrl** + **SHIFT** + **S** , aby zapisać pliki.

**Aby skonfigurować i skompilować projekt DLL:**

1. Na pasku narzędzi programu Visual Studio wybierz kolejno pozycje konfiguracja **debugowania** i platforma **x86** lub **x64** . Jeśli aplikacja wywołująca będzie platformą .NET Core, która jest zawsze uruchamiana w trybie 64-bitowym, wybierz opcję **x64** jako platformę.

1. W **Eksplorator rozwiązań**wybierz węzeł projektu **Mixed_Mode_Debugging** i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.

1. W górnej części okienka **Właściwości** upewnij się, że **Konfiguracja** jest ustawiona na **aktywna (Debuguj)** , a **platforma** jest taka sama jak ustawiona na pasku narzędzi: **x64**lub **Win32** dla platformy x86.

   > [!IMPORTANT]
   > Jeśli przełączysz platformę z **x86** na **x64** lub odwrotnie, musisz ponownie skonfigurować właściwości nowej platformy.

1. W obszarze **Właściwości konfiguracji** w lewym okienku wybierz pozycję **konsolidator**  >  **Advanced**i na liście rozwijanej obok **pozycji Brak punktu wejścia**wybierz pozycję **nie**. Jeśli trzeba było zmienić ją na **nie**, wybierz pozycję **Zastosuj**.

1. W obszarze **Właściwości konfiguracji**wybierz opcję **Ogólne**, a następnie na liście rozwijanej obok pozycji **Typ konfiguracji**wybierz pozycję **Biblioteka dynamiczna (dll)**. Wybierz pozycję **Apply** (Zastosuj), a następnie wybierz przycisk **OK**.

   ![Przełącz do natywnej biblioteki DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Wybierz projekt w **Eksplorator rozwiązań** a następnie wybierz pozycję **kompilacja**Kompiluj  >  **rozwiązanie**, naciśnij klawisz **F7**lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Kompiluj**.

   Projekt powinien być kompilowany bez błędów.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Tworzenie prostej zarządzanej aplikacji do wywoływania biblioteki DLL

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, **wpisz Console**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Aplikacja konsolowa (.NET Core)** lub **Aplikacja konsolowa (.NET Framework)** dla języka C#. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.

    Następnie wpisz nazwę, taką jak **Mixed_Mode_Calling_App** , i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C#** wybierz pozycję **Windows Desktop**, a następnie w środkowym okienku wybierz pozycję **Aplikacja konsolowa (.NET Framework)** lub **Aplikacja konsolowa (.NET Core)**.

    Następnie wpisz nazwę, taką jak **Mixed_Mode_Calling_App** , i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli szablon projektu **aplikacji konsolowej** nie jest widoczny, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie wybierz **Modyfikuj**.

    > [!NOTE]
    > Można również dodać nowy projekt zarządzany do istniejącego rozwiązania C++. Tworzymy projekt w nowym rozwiązaniu, aby zadanie debugowania w trybie mieszanym było trudniejsze.

   Program Visual Studio tworzy pusty projekt i wyświetla go w **Eksplorator rozwiązań**.

1. Zastąp cały kod w *program.cs* następującym kodem:

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

1. W nowym kodzie Zastąp ścieżkę pliku w `[DllImport]` ścieżce do pliku *Mixed_Mode_Debugging. dll* , który właśnie został utworzony. Zobacz komentarz do kodu, aby uzyskać wskazówki. Pamiętaj, aby zastąpić symbol zastępczy *nazwy użytkownika* .

1. Wybierz pozycję **plik**  >  **Zapisz program.cs** lub naciśnij **klawisze CTRL** + **S** , aby zapisać plik.

## <a name="configure-mixed-mode-debugging"></a>Konfigurowanie debugowania w trybie mieszanym

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Aby skonfigurować debugowanie w trybie mieszanym dla aplikacji .NET Framework

1. W **Eksplorator rozwiązań**wybierz węzeł projektu **Mixed_Mode_Calling_App** i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**.

1. W lewym okienku wybierz pozycję **Debuguj** , zaznacz pole wyboru **Włącz debugowanie kodu natywnego** , a następnie zamknij stronę właściwości, aby zapisać zmiany.

    ![Włącz debugowanie w trybie mieszanym](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Aby skonfigurować debugowanie w trybie mieszanym dla aplikacji .NET Core

W większości wersji programu Visual Studio, począwszy od programu Visual Studio 2017, należy użyć pliku *profilu launchsettings. JSON* zamiast właściwości projektu, aby włączyć debugowanie w trybie mieszanym dla kodu natywnego w aplikacji .NET Core. Aby śledzić aktualizacje interfejsu użytkownika dla tej funkcji, zobacz ten problem w usłudze [GitHub](https://github.com/dotnet/project-system/issues/1125).

1. W **Eksplorator rozwiązań**rozwiń węzeł **Właściwości**, a następnie otwórz plik *profilu launchsettings. JSON* .

   >[!NOTE]
   >Domyślnie *profilu launchsettings. JSON* znajduje się w *c:\users\username\source\repos\ Mixed_Mode_Calling_App \properties*. Jeśli *profilu launchsettings. JSON* nie istnieje, zaznacz projekt **Mixed_Mode_Calling_App** w **Eksplorator rozwiązań** a następnie wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. Wprowadź tymczasową zmianę na karcie **debugowanie** i skompiluj projekt. Spowoduje to utworzenie pliku *profilu launchsettings. JSON* . Przywróć zmianę dokonaną na karcie **debugowanie** .

1. W pliku *profilu launchsettings. JSON* Dodaj następujący wiersz:

    ```csharp
    "nativeDebugging": true
    ```

    Pełny plik będzie wyglądać podobnie do poniższego przykładu:

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

## <a name="set-a-breakpoint-and-start-debugging"></a>Ustaw punkt przerwania i Rozpocznij debugowanie

1. W projekcie C# Otwórz *program.cs*. Ustaw punkt przerwania w następującym wierszu kodu, klikając na marginesie po lewej stronie, wybierając wiersz i naciskając klawisz **F9**, lub klikając prawym przyciskiem myszy wiersz i wybierając **punkt przerwania**  >  **Wstaw punkt przerwania**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Czerwony okrąg pojawia się na lewym marginesie, na którym jest ustawiony punkt przerwania.

1. Naciśnij klawisz **F5**, wybierz zieloną strzałkę na pasku narzędzi programu Visual Studio lub wybierz pozycję **Debuguj**  >  **Rozpocznij debugowanie** , aby rozpocząć debugowanie.

   Debuger zatrzymuje się w ustawionym punkcie przerwania. Żółta strzałka wskazuje, gdzie debuger jest obecnie wstrzymany.

## <a name="step-in-and-out-of-native-code"></a>Wkroczenie i wyjście z kodu natywnego

1. Podczas gdy debugowanie jest wstrzymane w zarządzanej aplikacji, naciśnij klawisz **F11**lub wybierz pozycję **Debuguj**  >  **krok do**.

   Zostanie otwarty plik nagłówka natywnego *Mixed_Mode. h* , a zobaczysz żółtą strzałkę, w której debuger jest wstrzymany.

   ![Wkrocz do kodu natywnego](../debugger/media/mixed-mode-step-into-native-code.png)

1. Teraz można ustawiać i trafiać punkty przerwania oraz sprawdzać zmienne w kodzie macierzystym lub zarządzanym.

   - Umieść kursor nad zmiennymi w kodzie źródłowym, aby wyświetlić ich wartości.

   - Sprawdź zmienne i ich wartości w oknach **Autostart** i **Ustawienia regionalne** .

   - W debugerze można również użyć okien **czujki** i **stosu wywołań** .

1. Naciśnij ponownie klawisz **F11** , aby przejść do debugera o jeden wiersz.

1. Naciśnij klawisz **SHIFT** + **F11** lub wybierz pozycję **Debuguj**  >  **Wyjdź** , aby kontynuować wykonywanie i Wstrzymaj ponownie w zarządzanej aplikacji.

1. Naciśnij klawisz **F5** lub wybierz zieloną strzałkę, aby kontynuować debugowanie aplikacji.

Gratulacje! Ukończono samouczek dotyczący debugowania w trybie mieszanym.

## <a name="next-step"></a>Następny krok

W tym samouczku przedstawiono sposób debugowania kodu natywnego z zarządzanej aplikacji przez włączenie debugowania w trybie mieszanym. Aby zapoznać się z omówieniem innych funkcji debugera, zobacz:

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
