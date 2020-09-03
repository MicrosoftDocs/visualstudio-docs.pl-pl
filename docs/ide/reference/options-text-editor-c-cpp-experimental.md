---
title: Opcje, Edytor tekstów, C/C++, eksperymentalne
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 7e239ad3d2091f334f18ec00a367fc47d5c21db3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278700"
---
# <a name="options-text-editor-cc-experimental"></a>Opcje, Edytor tekstów, C/C++, eksperymentalne

Zmieniając te opcje, można zmienić zachowanie związane z technologią IntelliSense i bazą danych przeglądania podczas programowania w języku C lub C++. Te funkcje są naprawdę eksperymentalne i mogą być modyfikowane lub usuwane z programu Visual Studio w przyszłej wersji.

::: moniker range="vs-2017"

W tym artykule opisano opcje w programie Visual Studio 2017. W przypadku programu Visual Studio 2015 wybierz pozycję **2015** w selektorze powyżej spisu treści.

::: moniker-end

Aby uzyskać dostęp do tej strony właściwości, naciśnij klawisz **Ctrl** + **Q** , aby uaktywnić pole wyszukiwania, a następnie wpisz **eksperymentalne**. Wyszukiwanie znajduje się na stronie po kilku pierwszych literach. Możesz również uzyskać do niego dostęp, wybierając **Tools**  >  **Opcje** narzędzia i rozwinięcie **edytora tekstu**, a następnie **C/C++**, a następnie wybierając **eksperymentalne**.

Te funkcje są dostępne w instalacji programu Visual Studio.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Włącz technologię IntelliSense predykcyjną

Funkcja IntelliSense predykcyjna ogranicza liczbę wyników wyświetlanych na liście rozwijanej IntelliSense, dzięki czemu zobaczysz tylko wyniki, które są istotne w kontekście. Na przykład, jeśli wpiszesz `int x =` i wywołasz listę rozwijaną IntelliSense, zobaczysz tylko liczby całkowite lub funkcje, które zwracają liczby całkowite. Funkcja IntelliSense predykcyjna jest domyślnie wyłączona.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Włącz szybsze ładowanie projektu

Począwszy od programu Visual Studio 2017 w wersji 15,3, ta funkcja jest nazywana **Włącz buforowanie projektu** i została przeniesiona na stronę właściwości [Ustawienia projektu VC + +](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) .

Ta opcja umożliwia programowi Visual Studio buforowanie danych projektu w taki sposób, aby po otwarciu projektu za następnym razem można było załadować te dane w pamięci podręcznej, a nie ponownie obliczać je na podstawie plików projektu. Użycie danych w pamięci podręcznej może znacznie skrócić czas ładowania projektu.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Dodatkowe funkcje w Visual Studio Marketplace

W [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads)można przeglądać dodatkowe funkcje edytora tekstu. Przykładem są [szybkie poprawki w języku C++](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), które obsługują następujące elementy:

- **Dodaj brakujące #include** -proponuje odpowiednie #include dla nieznanych symboli w kodzie

- **Dodaj przy użyciu przestrzeni nazw/w pełni kwalifikujących się symboli** — podobnie jak w przypadku poprzedniego elementu, ale dla przestrzeni nazw

- **Dodaj brakujący średnik**

- **Pomoc online** — wyszukiwanie w pomocy online dotyczącej komunikatów o błędach

- I nie tylko...

## <a name="see-also"></a>Zobacz też

- [Ustawianie opcji Edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoryzacja w języku C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
