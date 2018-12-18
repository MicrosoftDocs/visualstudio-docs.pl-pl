---
title: Opcje, Edytor tekstu, C/C++, eksperymentalne
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 3f5ddf5a42199c8097e982c6ddd8e559185787fb
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672343"
---
# <a name="options-text-editor-cc-experimental"></a>Opcje, Edytor tekstu, C/C++, eksperymentalne

Zmieniając tych opcji, możesz zmienić zachowanie związane z technologii IntelliSense i bazy danych przeglądania w przypadku programowania w języku C lub C++. Te funkcje są naprawdę eksperymentalne i może modyfikację lub usunięta z programu Visual Studio w przyszłej wersji. W tym temacie opisano opcje w programie Visual Studio 2017. W programie Visual Studio 2015 wybierz **2015** w selektorze powyżej spisu treści.

Aby uzyskać dostęp do tej strony właściwości, naciśnij klawisze **Control + Q** aktywować `Quick Launch` , a następnie wpisz "eksperymentalne". Szybkie uruchamianie znajdzie strony po kilka pierwszych liter. Możesz również uzyskać do niego, wybierając **narzędzia | Opcje** i rozwijając **edytora tekstów**, następnie **C/C++**, a następnie wybierając **eksperymentalne**.

Te funkcje są dostępne w instalacji programu Visual Studio 2017.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Włączanie Predictive IntelliSense

Predictive IntelliSense ogranicza liczbę wyniki wyświetlane na liście rozwijanej funkcji IntelliSense, aby wyświetlić tylko wyniki, które są istotne w kontekście. Na przykład, jeśli wpiszesz <code>int x =</code> i wywołania funkcji IntelliSense listy rozwijanej, zostanie wyświetlony tylko liczby całkowite lub funkcji, które zwracają liczby całkowite. Predictive IntelliSense jest domyślnie wyłączona.

## <a name="enable-faster-project-load"></a>Włącz szybsze ładowanie projektu

**Visual Studio 2017 w wersji 15.3 lub nowszej**: Ta funkcja jest teraz nazywana **Włącz buforowanie projektu** przeniesiona do ikony [ustawienia projektu VC ++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) stronę właściwości.
Ta opcja umożliwia programu Visual Studio do buforowania danych projektu, dzięki czemu przy następnym otwarciu projektu go załadować tych buforowanych danych, zamiast ponownego przetwarzania danych z plików projektu. Przy użyciu danych z pamięci podręcznej można przyspieszyć czas ładowania projektu znacznie.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Dodatkowe funkcje w Visual Studio Marketplace

Możesz przeglądać funkcje edytora dodatkowy tekst w [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Na przykład [C++ szybkich poprawek](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), który obsługuje następujące czynności:

- **Dodaj brakujące #include** -sugeruje odpowiednie #include przez nieznany symboli w kodzie

- **Dodaj instrukcję using przestrzeń nazw/pełnej kwalifikacji symbol** — podobnie jak poprzedni element, ale w przypadku przestrzeni nazw

- **Dodaj Brak średnika**

- **Pomoc online** — wyszukiwanie Pomoc online, aby komunikaty o błędach

- i więcej...

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoryzacja języka C++ (VC Blog)](https://blogs.msdn.microsoft.com/vcblog/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview/)
