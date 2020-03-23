---
title: Wybieranie i instalowanie interpreterów języka Python
description: Pełna lista interpreterów języka Python, które są obsługiwane w programie Visual Studio z krótkimi instrukcjami, gdzie można znaleźć ich instalatorów.
ms.date: 06/05/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 13290aef7acfe599c7693af4be771c625e713596
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75735821"
---
# <a name="install-python-interpreters"></a>Instalowanie interpreterów języka Python

Domyślnie instalowanie obciążenia deweloperskiego języka Python w programie Visual Studio 2017, a później również instaluje Python 3 (64-bitowy). Opcjonalnie można zainstalować 32-bitowe i 64-bitowe wersje Pythona 2 i Pythona 3, wraz z Miniconda (Visual Studio 2019) lub Anaconda 2/Anaconda 3 (Visual Studio 2017), jak opisano w [instalacji](installing-python-support-in-visual-studio.md).

::: moniker range=">=vs-2019"
Alternatywnie można zainstalować standardowe interpretery języka python z okna dialogowego **Dodawanie środowiska.** Wybierz polecenie **Dodaj środowisko** w oknie Środowiska **języka Python** lub na pasku narzędzi Pythona, wybierz kartę **instalacji języka Python,** wskaż, które interpretery zainstalować, a następnie wybierz pozycję **Zainstaluj**.
::: moniker-end

Można również ręcznie zainstalować dowolny z interpreterów wymienionych w poniższej tabeli poza instalatorem programu Visual Studio. Na przykład jeśli zainstalowano anakondę 3 przed zainstalowaniem programu Visual Studio, nie trzeba go ponownie instalować za pośrednictwem instalatora programu Visual Studio. Interpreter można również zainstalować ręcznie, jeśli na przykład nowsza dostępna wersja, która nie jest jeszcze wyświetlana w instalatorze programu Visual Studio.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio obsługuje język Python w wersji 2.7, a także w wersji 3.5 i większej. Chociaż jest możliwe do edycji kodu napisanego w innych wersjach języka Python, te wersje nie są oficjalnie obsługiwane i funkcje, takie jak IntelliSense i debugowania może nie działać.
::: moniker-end

W programie **Visual Studio 2015 i starszym**programie należy ręcznie zainstalować jedną z interpreterów.

Visual Studio (wszystkie wersje) automatycznie wykrywa każdy zainstalowany interpreter Pythona i jego środowisko, sprawdzając rejestr zgodnie z [PEP 514 - Rejestracja Pythona w rejestrze systemu Windows](https://www.python.org/dev/peps/pep-0514/). Instalacje języka Python znajdują się zazwyczaj pod **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-bit) i **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-bit), a następnie w węzłach dystrybucji, takich jak **PythonCore** (CPython) i **ContinuumAnalytics** (Anaconda).

Jeśli program Visual Studio nie wykryje zainstalowanego środowiska, zobacz [Ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio pokazuje wszystkie znane środowiska w oknie [**Środowiska języka Python**](managing-python-environments-in-visual-studio.md#the-python-environments-window) i automatycznie wykrywa aktualizacje istniejących interpreterów.

| Interpreter | Opis |
| --- | --- |
| [CPython (Polski)](https://www.python.org/) | "Natywny" i najczęściej używany interpreter, dostępny w wersjach 32-bitowych i 64-bitowych (zalecane 32-bitowe). Zawiera najnowsze funkcje językowe, maksymalną kompatybilność pakietów Pythona, pełną obsługę debugowania i połączenie z [IPython](https://ipython.org/). Zobacz też: [Czy powinienem używać Pythona 2 lub Pythona 3?](https://wiki.python.org/moin/Python2orPython3). Należy zauważyć, że visual studio 2015 i wcześniej nie obsługują języka Python 3.6+ i może dać błędy, takie jak **nieobsługicony python w wersji 3.6**. Zamiast tego użyj języka Python 3.5 lub wcześniejszego. |
| [Boo](https://github.com/IronLanguages/ironpython2) | Implementacja .NET języka Python, dostępna w wersjach 32-bitowych i 64-bitowych, zapewniająca c#/F#/Visual Basic interop, dostęp do interfejsów API platformy .NET, standardowe debugowanie języka Python (ale nie debugowanie w trybie mieszanym C++) i mieszane debugowanie IronPython/C#. IronPython nie obsługuje jednak środowisk wirtualnych. |
| [Anaconda](https://www.continuum.io) | Platforma do nauki o otwartych danych obsługiwana przez Pythona i zawiera najnowszą wersję CPython i większość trudnych do zainstalowania pakietów. Polecamy, jeśli nie możesz w inny sposób zdecydować. |
| [PyPy (pypy)](https://www.pypy.org/) | Implementacja JIT o wysokiej wydajności języka Python, która jest dobra w przypadku długotrwałych programów i sytuacji, w których identyfikujesz problemy z wydajnością, ale nie można znaleźć innych rozwiązań. Współpracuje z programem Visual Studio, ale z ograniczoną obsługą zaawansowanych funkcji debugowania. |
| [Jython ( Jython )](https://www.jython.org/) | Implementacja języka Python na maszynie wirtualnej Java (JVM). Podobnie jak IronPython, kod uruchomiony w Jython może wchodzić w interakcje z klasami i bibliotekami Java, ale może nie być w stanie używać wielu bibliotek przeznaczonych dla CPython. Współpracuje z programem Visual Studio, ale z ograniczoną obsługą zaawansowanych funkcji debugowania. |

Deweloperzy, którzy chcą zapewnić nowe formy wykrywania dla środowisk Języka Python, zobacz [wykrywanie środowiska PTVS](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## <a name="move-an-interpreter"></a>Przenoszenie tłumacza

Jeśli przeniesiesz istniejący interpreter do nowej lokalizacji przy użyciu systemu plików, program Visual Studio nie wykryje automatycznie zmiany.

- Jeśli pierwotnie określono lokalizację interpretera za pośrednictwem okna **Środowiska języka Python,** następnie edytuj jego środowisko za pomocą karty **Konfiguruj** w tym oknie, aby zidentyfikować nową lokalizację. Zobacz [Ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Jeśli interpreter został zainstalowany przy użyciu programu instalacyjnego, użyj następujących kroków, aby ponownie zainstalować interpreter w nowej lokalizacji:

  1. Przywróć interpreter języka Python do jego pierwotnej lokalizacji.
  2. Odinstaluj interpreter za pomocą instalatora, który czyści wpisy rejestru.
  3. Zainstaluj ponownie interpreter w żądanej lokalizacji.
  4. Uruchom ponownie program Visual Studio, który powinien automatycznie wykryć nową lokalizację zamiast starej lokalizacji.

Po tym procesie gwarantuje, że wpisy rejestru, które identyfikują lokalizację interpretera, którego używa visual studio, są poprawnie aktualizowane. Za pomocą instalatora obsługuje również wszelkie inne skutki uboczne, które mogą istnieć.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie środowiskami języka Python](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna Środowiska języka Python](python-environments-window-tab-reference.md)
