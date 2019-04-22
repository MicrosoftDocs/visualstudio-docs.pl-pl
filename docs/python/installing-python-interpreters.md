---
title: Wybierz i zainstaluj interpretery języka Python
description: Pełna lista interpreterów języka Python, które są obsługiwane w programie Visual Studio z krótkie instrukcje, gdzie można znaleźć własnych instalatorów.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8e7648496e85b35d4f97fc9c85dc0bce6d17000e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59365226"
---
# <a name="install-python-interpreters"></a>Instalowanie interpreterów języka Python

Domyślnie instalowania obciążenia programowania języka Python w programie Visual Studio 2017 i nowszych wersjach instaluje Python 3 (wersja 64-bitowa). Opcjonalnie możesz zainstalować 32-bitowych i 64-bitowe wersje języka Python 2 i 3 języka Python, wraz z Miniconda (Visual Studio 2019) albo Anaconda 2/Anaconda 3 (Visual Studio 2017), zgodnie z opisem w [instalacji](installing-python-support-in-visual-studio.md).

::: moniker range=">=vs-2019"
Alternatywnie możesz zainstalować interpreterów standardowego języka python z **Dodaj środowisko** okna dialogowego. Wybierz **Dodaj środowisko** polecenia w pliku **środowiska Python** okna lub narzędzi języka Python wybierz **instalację języka Python** karcie wskazać, który tłumaczy do Zainstaluj i wybierz **zainstalować**.
::: moniker-end

Można też ręcznie zainstalują dowolną z interpretery wymienione w poniższej tabeli opisano poza Instalatora programu Visual Studio. Na przykład po zainstalowaniu pakietu Anaconda 3 przed zainstalowaniem programu Visual Studio, nie trzeba ponownie zainstalować za pomocą Instalatora programu Visual Studio. Można także zainstalować tłumacza ręcznie Jeśli, na przykład, nowsza wersja dostępna nie jeszcze są widoczne w Instalatorze programu Visual Studio.

Aby uzyskać **programu Visual Studio 2015 i starsze**, należy ręcznie zainstalować jeden interpretery.

Program Visual Studio (wszystkie wersje) automatycznie wykrywa interpreter języka Python i lokalne środowisko każdego zainstalowany, sprawdzając rejestru zgodnie z opisem w [514 program ten - Python rejestracji w rejestrze systemu Windows](https://www.python.org/dev/peps/pep-0514/). Instalacje języka Python, zwykle znajdują się w obszarze **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-bitowa) i **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-bitowy), następnie w ramach węzłów dla dystrybucja, takie jak **PythonCore** (CPython) i **ContinuumAnalytics** (Anaconda).

Jeśli program Visual Studio nie wykrywa zainstalowane środowisko, zobacz [ręcznie Zidentyfikuj istniejące środowisko](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio Wyświetla wszystkie znane środowisk w [ **środowiska Python** ](managing-python-environments-in-visual-studio.md#the-python-environments-window) okna i automatycznie wykrywa aktualizacje istniejących interpretery.

| Interpreter | Opis |
| --- | --- |
| [CPython](https://www.python.org/) | "Natywnego" i większości powszechnie stosowanych interpretera dostępne w wersjach 32-bitowych i 64-bitowych (32-bitowy zalecane). Obejmuje najnowsze funkcje języków, Maksymalna zgodność pakietu języka Python, pełna obsługa debugowania i współdziałanie z [IPython](https://ipython.org/). Zobacz też: [Należy używać języka Python 2 lub 3 języka Python? ](https://wiki,python.org/moin/Python2orPython3). Należy pamiętać, że Visual Studio 2015 i starsze nie obsługują środowiska Python 3.6 + i może spowodować błędy takie jak **nieobsługiwany języka python w wersji 3.6**. Korzystanie z języka Python w wersji 3.5 lub wcześniejszej zamiast tego. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implementacji .NET, języka Python, dostępne w wersjach 32-bitowych i 64-bitowych, zapewniając C#/F#/międzyoperacyjności języka Visual Basic, dostęp do interfejsów API platformy .NET, standardowego debugowania języka Python (ale nie C++ debugowanie w trybie mieszanym) i mieszane IronPython /C# debugowania. IronPython, jednak nie obsługuje środowisk wirtualnych. |
| [Anaconda](https://www.continuum.io) | Platforma analizy danych otwartych działającemu w języku Python i zawiera najnowszą wersję języka CPython i większość pakietów trudne do zainstalowania. Firma Microsoft zaleca Jeśli nie zdecydujesz inaczej. |
| [PyPy](https://www.pypy.org/) | Implementacja JIT śledzenia o wysokiej wydajności, środowiska Python, którą jest dobra dla programów długotrwałych i sytuacji, w której możesz zidentyfikować wydajności problemów, ale nie może znaleźć inne rozwiązania. Współpracuje z programem Visual Studio, ale z ograniczoną obsługę zaawansowanych funkcji debugowania. |
| [Jython](http://www.jython.org/) | Implementacja języka Python na maszynie wirtualnej Java (JVM). Podobnie jak IronPython, kod uruchomiony w Jython mogą wchodzić w interakcje z klasami Java i bibliotek, ale nie można używać wielu bibliotek przeznaczonych do języka CPython. Współpracuje z programem Visual Studio, ale z ograniczoną obsługę zaawansowanych funkcji debugowania. |

Deweloperzy, które chcą udostępniać nowe formy wykrywania dla środowiska Python, zobacz [wykrywania środowiska PTVS](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## <a name="move-an-interpreter"></a>Przenieś tłumacza

Jeśli przenosisz tłumacza istniejących do nowej lokalizacji w systemie plików, programu Visual Studio nie wykryje automatycznie zmiany.

- Jeśli pierwotnie określono lokalizację interpreter za pośrednictwem **środowiska Python** okna, należy edytować jego za pomocą środowiska **Konfiguruj** karty, w tym oknie, aby zidentyfikować nową lokalizację. Zobacz [ręcznie Zidentyfikuj istniejące środowisko](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Po zainstalowaniu interpreter przy użyciu programu instalacyjnego, użyj następujące kroki, ponownie zainstalować interpreter w nowej lokalizacji:

  1. Przywróć interpreter języka Python do jej oryginalnej lokalizacji.
  2. Odinstaluj interpreter przy użyciu jego Instalatora, który usuwa wpisy rejestru.
  3. Zainstaluj ponownie interpreter w żądanej lokalizacji.
  4. Uruchom ponownie Visual Studio, które powinny automatycznie wykrywać nowej lokalizacji zamiast w starej lokalizacji.

Po ten proces zapewnia, że wpisy rejestru, które identyfikują interpreter lokalizacji, która korzysta z programu Visual Studio, są zaktualizowane prawidłowo. Za pomocą Instalatora obsługuje także inne efekty uboczne, które mogą występować.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami Python](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
