---
title: Jak stosowane są ścieżki wyszukiwania języka Python
description: Visual Studio zapewnia bardziej szczegółowe środki, aby określić ścieżki wyszukiwania dla środowisk i projektów, aby uniknąć używania zmiennych dla całego systemu.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 37ce9d7b1853dfecc9e0ec33ca08c3c3fa0571e0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62428441"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Jak program Visual Studio używa ścieżek wyszukiwania języka Python

Przy typowym użyciu `PYTHONPATH` języka Python `IRONPYTHONPATH`zmienna środowiskowa (lub itp.) zapewnia domyślną ścieżkę wyszukiwania plików modułu. Oznacza to, że `from <name> import...` podczas `import <name>` korzystania z lub instrukcji, Python przeszukuje następujące lokalizacje w celu uzyskania pasującej nazwy:

1. Wbudowane moduły Pythona.
1. Folder zawierający uruchomiony kod Języka Python.
1. "Ścieżka wyszukiwania modułu" zdefiniowana przez odpowiednią zmienną środowiskową. (Zobacz [Ścieżka wyszukiwania modułu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) i [zmienne środowiskowe](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) w podstawowej dokumentacji języka Python).

Visual Studio ignoruje zmienną środowiskową ścieżki wyszukiwania, jednak nawet wtedy, gdy zmienna jest ustawiona dla całego systemu. Jest ignorowany właśnie *dlatego,* że jest ustawiony dla całego systemu i w ten sposób rodzi pewne pytania, na które nie można odpowiedzieć automatycznie: Czy odwołują się moduły przeznaczone dla Pythona 2.7 lub Pythona 3.6+? Czy zastąpią standardowe moduły biblioteki? Czy deweloper jest świadomy tego zachowania, czy jest to złośliwa próba porwania?

Visual Studio w ten sposób zapewnia środki do określania ścieżek wyszukiwania bezpośrednio w środowiskach i projektach. Kod, który można uruchomić lub debugować w programie `PYTHONPATH` Visual Studio odbiera ścieżki wyszukiwania w wartości (i innych równoważnych zmiennych). Dodając ścieżki wyszukiwania, visual studio sprawdza biblioteki w tych lokalizacjach i tworzy intellisense baz danych dla nich w razie potrzeby (Visual Studio 2017 w wersji 15.5 i wcześniejszych; tworzenie bazy danych może zająć trochę czasu w zależności od liczby bibliotek).

Aby dodać ścieżkę wyszukiwania, przejdź do **Eksploratora rozwiązań**, rozwiń węzeł projektu, kliknij prawym przyciskiem myszy **pozycję Szukaj ścieżek**, wybierz pozycję **Dodaj folder do ścieżki wyszukiwania:**

::: moniker range="vs-2017"
![Polecenie Dodaj folder do ścieżki wyszukiwania w ścieżkach wyszukiwania w Eksploratorze rozwiązań](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Polecenie Dodaj folder do ścieżki wyszukiwania w ścieżkach wyszukiwania w Eksploratorze rozwiązań](media/search-paths-command-2019.png)
::: moniker-end

To polecenie wyświetla przeglądarkę, w której następnie należy wybrać folder do uwzględnienia.

Jeśli `PYTHONPATH` zmienna środowiskowa zawiera już żądane foldery, użyj odpowiedniego skrótu **Dodaj ŚCIEŻKĘ PYTHONPATH do wyszukiwania.**

Po dodaniu folderów do ścieżek wyszukiwania program Visual Studio używa tych ścieżek dla dowolnego środowiska skojarzonego z projektem. (Mogą pojawić się błędy, jeśli środowisko jest oparte na Pythonie 3 i próbujesz dodać ścieżkę wyszukiwania do modułów Języka Python 2.7.

Pliki z rozszerzeniem *.zip* lub *.egg* można również dodać jako ścieżki wyszukiwania, wybierając polecenie **Dodaj archiwum zip do** ścieżki wyszukiwania. Podobnie jak w przypadku folderów, zawartość tych plików są skanowane i udostępniane intellisense.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie środowiskami języka Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Odwołanie do okna Środowiska języka Python](python-environments-window-tab-reference.md)
