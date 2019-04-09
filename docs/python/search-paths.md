---
title: Sposób stosowania ścieżki wyszukiwania języka Python
description: Program Visual Studio oferuje więcej określonych oznacza do określania ścieżek wyszukiwania dla środowisk i projektów, aby unikać używania zmiennych całego systemu.
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
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59365343"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Jak program Visual Studio używa ścieżki wyszukiwania języka Python

Za pomocą języka Python do typowy `PYTHONPATH` zmienna środowiskowa (lub `IRONPYTHONPATH`, itp.) zapewnia domyślna ścieżka wyszukiwania plików modułu. Oznacza to, kiedy używasz `from <name> import...` lub `import <name>` instrukcji, Python przeszukuje następujące lokalizacje o takiej samej nazwie:

1. Wbudowane moduły języka Python.
1. Folder zawierający kod języka Python działa.
1. "Moduł ścieżki wyszukiwania" jako zdefiniowanej przez zmienną środowiskową dotyczy. (Zobacz [ścieżki wyszukiwania modułu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) i [zmienne środowiskowe](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) w podstawowej dokumentacji języka Python.)

Program Visual Studio ignoruje wyszukiwania zmiennej środowiskowej path, jednak nawet wtedy, gdy zmienna jest ustawiana dla całego systemu. Jest on ignorowany, w rzeczywistości, dokładnie *ponieważ* jest ustawiona dla całego systemu i zgłasza w związku z tym niektóre kwestie, które nie odpowiedziano automatycznie: Są moduły odwołania przeznaczone dla środowiska Python 2.7 lub Python 3.6 +? Są one będą zastąpienia modułów biblioteki standardowej? Deweloper zdaje sobie sprawę z tego zachowania, czy jest próba złośliwego przejmującego?

Program Visual Studio udostępnia związku z tym oznacza, że do określania ścieżek wyszukiwania bezpośrednio w środowiskach i projektów. Kod, który uruchamiania lub debugowania w programie Visual Studio odbiera ścieżki wyszukiwania w wartości `PYTHONPATH` (i inne zmienne równoważne). Dodanie ścieżki wyszukiwania, Visual Studio sprawdza biblioteki w tych lokalizacjach i tworzy bazy danych IntelliSense dla ich w razie (Visual Studio 2017 w wersji 15.5 i starszych; tworzenia bazy danych może zająć trochę czasu w zależności od liczby bibliotek).

Aby dodać ścieżkę wyszukiwania, przejdź do **Eksploratora rozwiązań**, rozwiń węzeł projektu, kliknij prawym przyciskiem myszy **ścieżki wyszukiwania**, wybierz opcję **Dodaj Folder do ścieżki wyszukiwania**:

::: moniker range="vs-2017"
![Dodaj Folder do ścieżki wyszukiwania polecenia na ścieżki wyszukiwania w Eksploratorze rozwiązań](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dodaj Folder do ścieżki wyszukiwania polecenia na ścieżki wyszukiwania w Eksploratorze rozwiązań](media/search-paths-command-2019.png)
::: moniker-end

To polecenie wyświetla przeglądarki, w którym następnie wybierz folder do dołączenia.

Jeśli Twoje `PYTHONPATH` zmienna środowiskowa zawiera już foldery mają, użyj **PYTHONPATH Dodaj do ścieżki wyszukiwania** jako wygodny skrót.

Gdy foldery są dodawane do ścieżki wyszukiwania, Visual Studio używa tych ścieżek dla dowolnego środowiska skojarzony z projektem. (Może Zobacz błędy, jeśli środowisko jest oparty na środowisku Python 3, a następnie spróbujesz dodać ścieżkę wyszukiwania do modułów języka Python 2.7.)

Pliki z *zip* lub *.egg* rozszerzenia mogą być również dodawane jako ścieżki wyszukiwania, wybierając **Dodaj archiwum Zip do ścieżki wyszukiwania** polecenia. Podobnie jak w przypadku folderów, zawartość tych plików są skanowane i udostępniane funkcji IntelliSense.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
