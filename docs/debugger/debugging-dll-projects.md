---
title: Projekty dll debugowania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302204"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Biblioteki DLL debugowania w programie Visual Studio (C#, C++, Visual Basic, F#)

Biblioteka DLL (biblioteka łączy dynamicznych) to biblioteka zawierająca kod i dane, które mogą być używane przez więcej niż jedną aplikację. Za pomocą programu Visual Studio można tworzyć, tworzyć, konfigurować i debugować biblioteki DLL.

## <a name="create-a-dll"></a>Tworzenie biblioteki DLL

Następujące szablony projektów programu Visual Studio mogą tworzyć biblioteki DLL:

- Biblioteka klas języka C#, Visual Basic lub F#
- Biblioteka C# lub Visual Basic Windows Forms Control (WCF)
- Biblioteka dynamicznego łącza (DLL) języka C++

Aby uzyskać więcej informacji, zobacz [techniki debugowania MFC](../debugger/mfc-debugging-techniques.md).

Debugowanie biblioteki WCF jest podobny do debugowania biblioteki klas. Aby uzyskać szczegółowe informacje, zobacz [Formanty formularzy systemu Windows](/dotnet/framework/winforms/controls/index).

Zwykle wywołać bibliotekę DLL z innego projektu. Podczas debugowania projektu wywołującego, w zależności od konfiguracji biblioteki DLL, można wkroczyć i debugować kod DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Konfiguracja debugowania biblioteki DLL

Podczas tworzenia aplikacji za pomocą szablonu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu programu Visual Studio automatycznie tworzy wymagane ustawienia dla konfiguracji kompilacji debugowania i wydania. W razie potrzeby można zmienić te ustawienia. Aby uzyskać więcej informacji zobacz następujące artykuły:

- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Ustawienia projektu dla konfiguracji debugowania języka C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Jak: Ustawianie konfiguracji debugowania i zwalniania](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Set C++ DebuggableAttribute

Aby debuger dołączyć do biblioteki DLL języka C++, `DebuggableAttribute`kod C++ musi emitować .

**Aby `DebuggableAttribute`ustawić:**

1. Wybierz projekt biblioteki DLL języka C++ w **Eksploratorze rozwiązań** i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

1. W okienku **Właściwości** w obszarze**Debugowanie** **konsolidatora** > wybierz pozycję **Tak (/ASSEMBLYDEBUG)** dla **zestawu debugowania**.

Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>Ustawianie lokalizacji plików DLL języka C/C++

Aby debugować zewnętrzną bibliotekę DLL, projekt wywołujący musi być w stanie znaleźć bibliotekę DLL, jej [plik pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)i wszystkie inne pliki, które wymaga biblioteki DLL. Można utworzyć zadanie kompilacji niestandardowej, aby skopiować te pliki do * \<folderu projektu>\Debug* folderu wyjściowego lub skopiować pliki tam ręcznie.

W przypadku projektów C/C++ można ustawić lokalizacje plików nagłówka i LIB na stronach właściwości projektu, zamiast kopiować je do folderu wyjściowego.

**Aby ustawić lokalizacje plików nagłówka C/C++ i LIB:**

1. Wybierz projekt DLL języka C/C++ w **Eksploratorze rozwiązań** i wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

1. U góry okienka **Właściwości** w obszarze **Konfiguracja**wybierz pozycję **Wszystkie konfiguracje**.

1. W obszarze Dodatkowe**katalogi dołączania****ogólne** >  **C/C++** > określ folder zawierający pliki nagłówkowe.

1. W obszarze**General** > **Katalogi dodatkowych bibliotek dodatkowych** **linkera** > określ folder zawierający pliki LIB.

1. W obszarze Dodatkowe zależności**wejściowe** >  **konsolidatora** > określ pełną ścieżkę i nazwę pliku dla plików LIB.**Additional Dependencies**

1. Kliknij przycisk **OK**.

Aby uzyskać więcej informacji na temat ustawień projektu języka C++, zobacz [Odwołanie do strony właściwości systemu Windows C++](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Tworzenie wersji debugowania

Upewnij się, aby utworzyć wersję debugowania biblioteki DLL przed rozpoczęciem debugowania. Aby debugować bibliotekę DLL, aplikacja wywołująca musi być w stanie znaleźć jej [plik pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) i wszystkie inne pliki, które wymaga biblioteki DLL.

Można utworzyć niestandardowe zadanie kompilacji, aby skopiować pliki DLL do * \<folderu projektu wywołującego>\Debug* folderu wyjściowego lub skopiować pliki tam ręcznie.

Upewnij się, że wywołanie biblioteki DLL w jego poprawnej lokalizacji. Może się to wydawać oczywiste, ale jeśli aplikacja wywołująca znajdzie i ładuje inną kopię biblioteki DLL, debuger nigdy nie trafi ustawionych punktów przerwania.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Debugowanie biblioteki DLL

Nie można uruchomić biblioteki DLL bezpośrednio. Musi być wywoływana przez aplikację, zwykle plik *.exe.* Aby uzyskać więcej informacji, zobacz [Projekty programu Visual Studio — C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Aby debugować bibliotekę DLL, można [rozpocząć debugowanie z aplikacji wywołującej](#vxtskdebuggingdllprojectsthecallingapplication)lub [debugowania z projektu biblioteki DLL,](how-to-debug-from-a-dll-project.md) określając jego aplikacji wywołującej. Można również użyć [debugera natychmiastowe okno](#vxtskdebuggingdllprojectstheimmediatewindow) do oceny funkcji DLL lub metod w czasie projektowania, bez użycia aplikacji wywołującej.

Aby uzyskać więcej informacji, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Rozpoczynanie debugowania z aplikacji wywołującej

Aplikacja, która wywołuje bibliotekę DLL może być:

- Aplikacja z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu w tym samym lub innym rozwiązaniu z biblioteki DLL.
- Istniejąca aplikacja, która jest już wdrożona i uruchomiona na komputerze testowym lub produkcyjnym.
- Znajduje się w internecie i dostępne za pośrednictwem adresu URL.
- Aplikacja internetowa ze stroną sieci Web, która osadza bibliotekę DLL.

Aby debugować bibliotekę DLL z aplikacji wywołującej, można:

- Otwórz projekt dla aplikacji wywołującej i rozpocznij debugowanie, wybierając **debugowanie** > **start debugowania** lub naciskając **klawisz F5**.

  lub

- Dołącz do aplikacji, która jest już wdrożona i uruchomiona na komputerze testowym lub produkcyjnym. Użyj tej metody dla bibliotek DLL w witrynach sieci Web lub w aplikacjach internetowych. Aby uzyskać więcej informacji, zobacz [Jak: Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Przed rozpoczęciem debugowania aplikacji wywołującej, należy ustawić punkt przerwania w dll. Zobacz [Korzystanie z punktów przerwania](../debugger/using-breakpoints.md). Po trafieniu punktu przerwania biblioteki DLL można przejść przez kod, obserwując akcję w każdym wierszu. Aby uzyskać więcej informacji, zobacz [Nawigowanie po kodzie w debugerze](../debugger/navigating-through-code-with-the-debugger.md).

Podczas debugowania można użyć okna **Moduły,** aby zweryfikować biblioteki DLL i pliki *exe,* które aplikacja ładuje. Aby otworzyć okno **Moduły** podczas debugowania, wybierz opcję **Debugowanie** > **modułów****systemu Windows** > . Aby uzyskać więcej informacji, zobacz [Jak: Użyj okna Moduły](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Użyj okna Natychmiastowe

Za pomocą okna **Natychmiastowe** można ocenić funkcje biblioteki DLL lub metody w czasie projektowania. Okno **Bezpośrednie** odgrywa rolę aplikacji wywołującej.

>[!NOTE]
>Okna **Natychmiastowe** można użyć w czasie projektowania z większością typów projektów. Nie jest obsługiwany dla sql, projektów internetowych lub skryptu.

Na przykład, aby przetestować metodę o nazwie `Test` w klasie: `Class1`

1. Po otwarciu projektu biblioteki DLL otwórz okno **Natychmiastowe,** wybierając **pozycję Debug** > **Windows** > **Immediate** lub naciskając **klawisze Ctrl**+**Alt**+**I**.

1. Tworzenie wystąpienia obiektu typu, `Class1` wpisując następujący kod C# w oknie **Natychmiastowe** i naciskając klawisz **Enter**. Ten kod zarządzany działa dla języka C# i Visual Basic, z odpowiednimi zmianami składni:

   ```csharp
   Class1 obj = new Class1();
   ```

   W języku C#wszystkie nazwy muszą być w pełni kwalifikowane. Wszelkie metody lub zmienne muszą znajdować się w bieżącym zakresie i kontekście, gdy usługa języka próbuje ocenić wyrażenie.

1. Zakładając, `Test` że `int` przyjmuje `Test` jeden parametr, oceń za pomocą okna **Natychmiastowe:**

   ```csharp
   ?obj.Test(10);
   ```

   Wynik zostanie wydrukowany w oknie **Natychmiastowy.**

1. Można kontynuować debugowanie, `Test` umieszczając punkt przerwania wewnątrz niego, a następnie oceniając funkcję ponownie.

   Punkt przerwania zostanie trafiony i można `Test`przejść przez . Po wykonaniu `Test`opuścił debuger powróci w trybie projektowania.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Debugowanie w trybie mieszanym

Można napisać aplikację wywołującą dla biblioteki DLL w kodzie zarządzanym lub natywnym. Jeśli aplikacja natywna wywołuje zarządzaną bibliotekę DLL i chcesz debugować oba, można włączyć debugery zarządzane i natywne we właściwościach projektu. Dokładny proces zależy od tego, czy chcesz rozpocząć debugowanie z projektu biblioteki DLL lub wywołującego projektu aplikacji. Aby uzyskać więcej informacji, zobacz [Jak: Debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).

Można również debugować natywną bibliotekę DLL z zarządzanego projektu wywołującego. Aby uzyskać więcej informacji, zobacz [Jak debugować kod zarządzany i natywny](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Przygotowanie do debugowania projektów języka C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Ustawienia projektu dla konfiguracji debugowania języka C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania języka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
