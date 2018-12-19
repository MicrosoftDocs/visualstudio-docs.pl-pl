---
title: Sposób stosowania ścieżki wyszukiwania języka Python
description: Omówienie, jak program Visual Studio używa języka Python ścieżki wyszukiwania, zarówno w środowiskach, jak i w projektach.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 92185b224af50dd5cf125d62282f1e8f7b951bc6
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349003"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Jak program Visual Studio używa ścieżki wyszukiwania języka Python

Za pomocą języka Python do typowy `PYTHONPATH` zmienna środowiskowa (lub `IRONPYTHONPATH`, itp.) zapewnia domyślna ścieżka wyszukiwania plików modułu. Oznacza to, kiedy używasz `from <name> import...` lub `import <name>` instrukcji, Python przeszukuje następujące lokalizacje o takiej samej nazwie:

1. Wbudowane moduły języka Python.
1. Folder zawierający kod języka Python działa.
1. "Moduł ścieżki wyszukiwania" jako zdefiniowanej przez zmienną środowiskową dotyczy. (Zobacz [ścieżki wyszukiwania modułu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) i [zmienne środowiskowe](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) w podstawowej dokumentacji języka Python.)

Program Visual Studio ignoruje wyszukiwania zmiennej środowiskowej path, jednak nawet wtedy, gdy zmienna jest ustawiana dla całego systemu. Jest on ignorowany, w rzeczywistości, dokładnie *ponieważ* jest ustawiona dla całego systemu i zgłasza w związku z tym niektóre kwestie, które nie odpowiedziano automatycznie: to moduły odwołania, przeznaczona dla środowiska Python 2.7 lub Python 3.6 +? Są one będą zastąpienia modułów biblioteki standardowej? Deweloper zdaje sobie sprawę z tego zachowania, czy jest próba złośliwego przejmującego?

Program Visual Studio udostępnia związku z tym oznacza, że do określania ścieżek wyszukiwania bezpośrednio w środowiskach i projektów. Kod, który uruchamiania lub debugowania w programie Visual Studio odbiera ścieżki wyszukiwania w wartości `PYTHONPATH` (i inne zmienne równoważne). Dodanie ścieżki wyszukiwania, Visual Studio sprawdza biblioteki w tych lokalizacjach i tworzy bazy danych IntelliSense dla ich w razie (Visual Studio 2017 w wersji 15.5 i starszych; tworzenia bazy danych może zająć trochę czasu w zależności od liczby bibliotek).

Aby dodać ścieżkę wyszukiwania, kliknij prawym przyciskiem myszy **ścieżki wyszukiwania** pozycja **Eksploratora rozwiązań**, wybierz opcję **Dodaj Folder do ścieżki wyszukiwania**i wybierz folder, aby uwzględnić. Ta ścieżka jest używana dla dowolnego środowiska skojarzony z projektem. (Może Zobacz błędy, jeśli środowisko jest oparty na środowisku Python 3, a następnie spróbujesz dodać ścieżkę wyszukiwania do modułów języka Python 2.7.)

Pliki z *zip* lub *.egg* rozszerzenia mogą być również dodawane jako ścieżki wyszukiwania, wybierając **Dodaj archiwum Zip do ścieżki wyszukiwania**. Podobnie jak w przypadku folderów, zawartość tych plików są skanowane i udostępniane funkcji IntelliSense.

Jeśli zawartość nie zmienia się często regularnie używasz tej samej ścieżki wyszukiwania, może być bardziej efektywne i zainstaluj go w folderze pakietów lokacji. Ścieżka wyszukiwania są następnie analizowane i przechowywane w bazie danych technologii IntelliSense, zawsze jest skojarzony ze środowiskiem zamierzone i nie wymaga ścieżki wyszukiwania, który ma zostać dodany do każdego projektu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
