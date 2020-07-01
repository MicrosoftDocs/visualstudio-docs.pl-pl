---
title: Jak są stosowane ścieżki wyszukiwania w języku Python
description: Program Visual Studio zapewnia bardziej szczegółowy sposób określania ścieżek wyszukiwania dla środowisk i projektów, aby uniknąć używania zmiennych systemowych.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3a23afff970405bf7ae1bbd1c8aad326eb133780
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520383"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Jak program Visual Studio używa ścieżek wyszukiwania języka Python

W przypadku typowego użycia języka Python `PYTHONPATH` zmienna środowiskowa (lub `IRONPYTHONPATH` itp.) zapewnia domyślną ścieżkę wyszukiwania dla plików modułów. Oznacza to, że w przypadku użycia `from <name> import...` `import <name>` instrukcji or, środowisko Python przeszukuje następujące lokalizacje w celu uzyskania zgodnej nazwy:

1. Wbudowane moduły języka Python.
1. Folder zawierający kod języka Python, który jest uruchomiony.
1. "Ścieżka wyszukiwania modułu" zgodnie z definicją w odpowiedniej zmiennej środowiskowej. (Zobacz [ścieżki wyszukiwania modułu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) i [zmienne środowiskowe](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) w podstawowej dokumentacji języka Python).

Program Visual Studio ignoruje zmienną środowiskową ścieżki wyszukiwania, jednak nawet jeśli zmienna jest ustawiona dla całego systemu. Jest ona ignorowana, w rzeczywistości, *ponieważ* jest ustawiona dla całego systemu i w ten sposób wywołuje pewne pytania, na które nie można udzielić odpowiedzi automatycznie: czy są to moduły, do których odwołuje się język Python 2,7 lub Python 3.6 +? Czy chcesz przesłonić standardowe moduły biblioteki? Czy deweloperzy są świadomi tego zachowania, czy jest to złośliwa próba przejęcia?

W związku z tym program Visual Studio umożliwia określenie ścieżek wyszukiwania bezpośrednio w środowiskach i projektach. Kod uruchamiany lub Debuguj w programie Visual Studio otrzymuje ścieżki wyszukiwania w wartości `PYTHONPATH` (i innych równoważnych zmiennych). Po dodaniu ścieżek wyszukiwania program Visual Studio sprawdza biblioteki w tych lokalizacjach i kompiluje bazy danych IntelliSense dla nich, gdy jest to potrzebne (Visual Studio 2017 w wersji 15,5 i starszej). konstruowanie bazy może zająć trochę czasu w zależności od liczby bibliotek.

Aby dodać ścieżkę wyszukiwania, przejdź do **Eksplorator rozwiązań**, rozwiń węzeł projektu, kliknij prawym przyciskiem myszy pozycję **ścieżki wyszukiwania**, wybierz polecenie **Dodaj folder do ścieżki wyszukiwania**:

::: moniker range="vs-2017"
![Dodaj folder do polecenia przeszukiwania ścieżki na ścieżce wyszukiwania w Eksplorator rozwiązań](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dodaj folder do polecenia przeszukiwania ścieżki na ścieżce wyszukiwania w Eksplorator rozwiązań](media/search-paths-command-2019.png)
::: moniker-end

To polecenie wyświetla przeglądarkę, w której można wybrać folder do uwzględnienia.

Jeśli `PYTHONPATH` zmienna środowiskowa zawiera już żądane foldery, użyj **Dodaj PYTHONPATH, aby wyszukać ścieżki** jako wygodny skrót.

Po dodaniu folderów do ścieżek wyszukiwania program Visual Studio używa tych ścieżek dla każdego środowiska skojarzonego z projektem. (Mogą pojawić się błędy, jeśli środowisko jest oparte na języku Python 3 i podjęto próbę dodania ścieżki wyszukiwania do modułów języka Python 2,7).

Pliki z rozszerzeniem *zip* lub *jajka* można również dodać jako ścieżki wyszukiwania, wybierając pozycję **Dodaj archiwum zip do ścieżki wyszukiwania** . Podobnie jak w przypadku folderów, zawartość tych plików jest skanowana i udostępniana w technologii IntelliSense.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami języka Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
