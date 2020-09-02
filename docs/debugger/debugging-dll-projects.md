---
title: Debuguj projekty DLL | Microsoft Docs
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315073"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Debugowanie bibliotek DLL w programie Visual Studio (C#, C++, Visual Basic, F #)

DLL (biblioteka dołączana dynamicznie) to biblioteka, która zawiera kod i dane, które mogą być używane przez więcej niż jedną aplikację. Za pomocą programu Visual Studio można tworzyć, kompilować, konfigurować i debugować biblioteki DLL.

## <a name="create-a-dll"></a>Tworzenie biblioteki DLL

Następujące szablony projektów programu Visual Studio mogą tworzyć biblioteki dll:

- Biblioteka klas C#, Visual Basic lub F #
- Biblioteka formantów Windows Forms C# lub Visual Basic (WCF)
- Biblioteka dołączana dynamicznie (DLL) języka C++

Aby uzyskać więcej informacji, zobacz [techniki debugowania MFC](../debugger/mfc-debugging-techniques.md).

Debugowanie biblioteki WCF jest podobne do debugowania biblioteki klas. Aby uzyskać szczegółowe informacje, zobacz [Windows Forms Controls](/dotnet/framework/winforms/controls/index).

Zazwyczaj wywoływana jest biblioteka DLL z innego projektu. Podczas debugowania projektu wywołującego, w zależności od konfiguracji biblioteki DLL, można wkroczyć i debugować kod DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Konfiguracja debugowania DLL

W przypadku tworzenia aplikacji za pomocą szablonu projektu programu Visual Studio program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie tworzy wymagane ustawienia dla konfiguracji debugowania i wydania kompilacji. W razie potrzeby możesz zmienić te ustawienia. Aby uzyskać więcej informacji, zobacz następujące artykuły:

- [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Instrukcje: Ustawianie konfiguracji debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Set C++ DebuggableAttribute

Aby debuger mógł dołączyć do biblioteki DLL języka C++, kod języka C++ musi emitować `DebuggableAttribute` .

**Aby ustawić `DebuggableAttribute` :**

1. Wybierz projekt biblioteki DLL C++ w **Eksplorator rozwiązań** i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

1. W okienku **Właściwości** w obszarze Debugowanie **konsolidatora**  >  **Debugging**wybierz pozycję **tak (/ASSEMBLYDEBUG)** dla **zestawu możliwością debugowania**.

Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> Ustaw lokalizacje plików DLL C/C++

Aby debugować zewnętrzną bibliotekę DLL, wywołujący projekt musi być w stanie znaleźć bibliotekę DLL, jej [plik. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)oraz inne pliki wymagane przez bibliotekę DLL. Można utworzyć niestandardowe zadanie kompilacji, aby skopiować te pliki do folderu wyjściowego * \<project folder> \debug.* lub ręcznie skopiować pliki.

W przypadku projektów C/C++ można ustawić nagłówki i lokalizacje plików LIB na stronach właściwości projektu, zamiast kopiować je do folderu wyjściowego.

**Aby ustawić lokalizację nagłówka C/C++ i plików LIB:**

1. Wybierz projekt DLL C/C++ w **Eksplorator rozwiązań** i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

1. W górnej części okienka **Właściwości** w obszarze **Konfiguracja**wybierz pozycję **wszystkie konfiguracje**.

1. W obszarze Ogólne **C/C++**  >  **General**  >  **Dodatkowe katalogi dołączania**określ folder, w którym znajdują się pliki nagłówkowe.

1. W obszarze **konsolidator**  >  **Ogólne**  >  **dodatkowe biblioteki katalogi**określ folder, w którym znajdują się pliki lib.

1. W **obszarze**dołączanie  >  **Input**  >  **dodatkowe zależności**wprowadź pełną ścieżkę i nazwę pliku dla plików lib.

1. Wybierz pozycję **OK**.

Aby uzyskać więcej informacji na temat ustawień projektu C++, zobacz [informacje na stronie właściwości systemu Windows C++](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Kompiluj wersję do debugowania

Przed rozpoczęciem debugowania upewnij się, że została utworzona wersja debugowania biblioteki DLL. Aby debugować bibliotekę DLL, aplikacja wywołująca musi być w stanie znaleźć swój [plik. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) oraz inne pliki wymagane przez bibliotekę DLL.

Można utworzyć niestandardowe zadanie kompilacji w celu skopiowania plików DLL do folderu wyjściowego * \<calling project folder> \debug.* lub ręcznie skopiować pliki.

Upewnij się, że plik DLL jest wywoływany w prawidłowej lokalizacji. Może wydawać się oczywiste, ale jeśli aplikacja wywołująca znajdzie i załaduje inną kopię biblioteki DLL, debuger nigdy nie osiągnie ustawionych punktów przerwania.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Debugowanie biblioteki DLL

Nie można bezpośrednio uruchomić biblioteki DLL. Musi być wywoływana przez aplikację, zazwyczaj plik *. exe* . Aby uzyskać więcej informacji, zobacz [Visual Studio projects — C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Aby debugować bibliotekę DLL, można [rozpocząć debugowanie z aplikacji wywołującej](#vxtskdebuggingdllprojectsthecallingapplication)lub [DEBUGOWAĆ z projektu DLL](how-to-debug-from-a-dll-project.md) przez określenie jego aplikacji wywołującej. Można również użyć [natychmiastowego okna](#vxtskdebuggingdllprojectstheimmediatewindow) debugera do oszacowania funkcji lub metod biblioteki DLL w czasie projektowania bez użycia aplikacji wywołującej.

Aby uzyskać więcej informacji, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Rozpocznij debugowanie z aplikacji wywołującej

Aplikacja, która wywołuje bibliotekę DLL, może:

- Aplikacja z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu w tym samym lub innym rozwiązaniu z biblioteki DLL.
- Istniejąca aplikacja, która została już wdrożona i uruchomiona na komputerze testowym lub produkcyjnym.
- Znajdujący się w sieci Web i dostęp za pomocą adresu URL.
- Aplikacja internetowa ze stroną sieci Web, która osadza bibliotekę DLL.

Aby debugować bibliotekę DLL z aplikacji wywołującej, możesz:

- Otwórz projekt dla aplikacji wywołującej i Rozpocznij debugowanie, wybierając pozycję **Debuguj**  >  **Rozpocznij debugowanie** lub naciskając klawisz **F5**.

  lub

- Dołącz do aplikacji, która została już wdrożona i uruchomiona na komputerze testowym lub produkcyjnym. Tej metody należy użyć w przypadku bibliotek DLL w witrynach sieci Web lub w aplikacjach internetowych. Aby uzyskać więcej informacji, zobacz [jak: dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Przed rozpoczęciem debugowania aplikacji wywołującej Ustaw punkt przerwania w bibliotece DLL. Zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md). Po trafieniu punktu przerwania biblioteki DLL można przejść przez kod, obserwując akcję w każdym wierszu. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie w debugerze](../debugger/navigating-through-code-with-the-debugger.md).

Podczas debugowania można użyć okna **moduły** do zweryfikowania plików DLL i *exe* ładowanych przez aplikację. Aby otworzyć okno **moduły** , podczas debugowania wybierz kolejno opcje **Debuguj**  >  moduły**systemu Windows**  >  **Modules**. Aby uzyskać więcej informacji, zobacz [How to: Use the modules Window](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Korzystanie z okna bezpośredniego

Możesz użyć **bezpośredniego** okna do szacowania funkcji lub metod biblioteki DLL w czasie projektowania. Okno **bezpośrednie** odgrywa rolę aplikacji wywołującej.

>[!NOTE]
>Możesz użyć okna **bezpośredniego** w czasie projektowania z większością typów projektów. Nie jest to obsługiwane w przypadku programu SQL, projektów sieci Web ani skryptu.

Na przykład, aby przetestować metodę o nazwie `Test` w klasie `Class1` :

1. Po otwarciu projektu DLL Otwórz okno **bezpośrednie** , wybierając pozycję **Debuguj**  >  **Windows**  >  **natychmiastowe** lub naciskając **klawisze CTRL** + **Alt** + **I**.

1. Utwórz wystąpienie obiektu typu `Class1` , wpisując następujący kod w języku C# w oknie **bezpośrednim** i naciskając klawisz **Enter**. Ten kod zarządzany działa dla języków C# i Visual Basic z odpowiednimi zmianami składni:

   ```csharp
   Class1 obj = new Class1();
   ```

   W języku C# wszystkie nazwy muszą być w pełni kwalifikowane. Wszelkie metody lub zmienne muszą znajdować się w bieżącym zakresie i kontekście, gdy usługa języka próbuje oszacować wyrażenie.

1. Przy założeniu, że `Test` przyjmuje jeden `int` parametr, Oceń `Test` przy użyciu okna **bezpośredniego** :

   ```csharp
   ?obj.Test(10);
   ```

   Wynik zostanie wydrukowany w oknie **bezpośrednim** .

1. Można kontynuować debugowanie `Test` , umieszczając w niej punkt przerwania, a następnie ponownie obliczając funkcję.

   Punkt przerwania zostanie trafiony i możesz przejść do niego `Test` . Po `Test` powrocie wykonania debuger zostanie przywrócony do trybu projektowania.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debugowanie w trybie mieszanym

Można napisać aplikację wywołującą dla biblioteki DLL w kodzie zarządzanym lub natywnym. Jeśli aplikacja natywna wywołuje zarządzaną bibliotekę DLL i chcesz debugować obie te elementy, można włączyć zarówno debugery zarządzane, jak i natywne we właściwościach projektu. Dokładny proces zależy od tego, czy chcesz rozpocząć debugowanie z projektu DLL lub projektu aplikacji wywołującej. Aby uzyskać więcej informacji, zobacz [jak: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).

Można również debugować natywną bibliotekę DLL z zarządzanego projektu wywołującego. Aby uzyskać więcej informacji, zobacz [jak debugować kod zarządzany i natywny](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Przygotowanie do debugowania projektów C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Typy projektów C#, F # i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
