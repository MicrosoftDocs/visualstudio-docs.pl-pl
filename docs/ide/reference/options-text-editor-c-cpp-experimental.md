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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278700"
---
# <a name="options-text-editor-cc-experimental"></a>Opcje, Edytor tekstów, C/C++, eksperymentalne

Zmieniając te opcje, można zmienić zachowanie związane z IntelliSense i przeglądania bazy danych podczas programowania w języku C lub C++. Te funkcje są naprawdę eksperymentalne i mogą być modyfikowane lub usuwane z programu Visual Studio w przyszłej wersji.

::: moniker range="vs-2017"

W tym artykule opisano opcje w programie Visual Studio 2017. W programie Visual Studio 2015 wybierz **2015** w selektorze powyżej spisu treści.

::: moniker-end

Aby uzyskać dostęp do tej strony właściwości, naciśnij **klawisz Ctrl**+**Q,** aby aktywować pole wyszukiwania, a następnie wpisz **eksperymentalne**. Wyszukiwanie znajduje stronę po pierwszych kilku literach. Można również uzyskać do niego dostęp, wybierając**opcję Opcje** **narzędzi** > i rozwiń **edytor tekstu**, następnie **C/C++,** a następnie wybierając **opcję Eksperymentalne.**

Te funkcje są dostępne w instalacji programu Visual Studio.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [Personalizuj IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Włącz predykcyjny intellisense

Predictive IntelliSense ogranicza liczbę wyników wyświetlanych na liście rozwijanej IntelliSense, dzięki czemu są wyświetlane tylko wyniki, które są istotne w kontekście. Na przykład jeśli `int x =` wpiszesz i wywołasz intellisense rozwijanej, zobaczysz tylko liczby całkowite lub funkcje, które zwracają liczby całkowite. Predictive IntelliSense jest domyślnie wyłączony.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Szybsze ładowanie projektu

Od programu Visual Studio 2017 w wersji 15.3 ta funkcja nosi nazwę **Włącz buforowanie projektu** i została przeniesiona na stronę właściwości [Ustawienia projektu VC++.](vcpp-project-settings-projects-and-solutions-options-dialog-box.md)

Ta opcja umożliwia programowi Visual Studio buforowanie danych projektu, dzięki czemu po otwarciu projektu następnym razem można załadować te dane w pamięci podręcznej, a nie ponownego obliczania go z plików projektu. Korzystanie z danych w pamięci podręcznej może znacznie przyspieszyć czas ładowania projektu.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Dodatkowe funkcje w portalu Visual Studio Marketplace

Dodatkowe funkcje edytora tekstu można przeglądać w programie [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Przykładem jest [C++ Quick Fixes](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), który obsługuje następujące czynności:

- **Dodaj brakujące #include** - Sugeruje odpowiednie #include dla nieznanych symboli w kodzie

- **Dodaj przy użyciu obszaru nazw/W pełni kwalifikują się symbol** - Podobnie jak poprzedni element, ale dla obszarów nazw

- **Dodawanie brakującego średnika**

- **Pomoc online** - Szukaj pomocy online dla komunikatów o błędach

- I więcej...

## <a name="see-also"></a>Zobacz też

- [Ustawianie opcji Edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoryzowanie w języku C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
