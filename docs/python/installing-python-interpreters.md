---
title: Wybierz i zainstaluj interpretery języka Python
description: Kompletna lista interpreterów języka Python, które są obsługiwane w programie Visual Studio z krótkimi instrukcjami dotyczącymi lokalizacji instalacji.
ms.date: 06/05/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b91d18fe5924abe12240f31295b4853c1e932333
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984619"
---
# <a name="install-python-interpreters"></a>Instalowanie interpreterów języka Python

Domyślnie zainstalowanie obciążenia programowania w języku Python w programie Visual Studio 2017 lub nowszym powoduje także instalację języka Python 3 (64-bit). Opcjonalnie można zainstalować 32-bitowe i 64-bitowe wersje języków Python 2 i Python 3 oraz Miniconda (Visual Studio 2019) lub Anaconda 2/Anaconda 3 (Visual Studio 2017), zgodnie z opisem w [instalacji](installing-python-support-in-visual-studio.md).

::: moniker range=">=vs-2019"
Alternatywnie można zainstalować standardowe interpretery języka Python z okna dialogowego **Dodawanie środowiska** . Wybierz polecenie **Dodaj środowisko** w oknie **środowiska Python** lub na pasku narzędzi Python, wybierz kartę **Instalacja języka Python** , wskaż, które interpretery zainstalować, a następnie wybierz pozycję **Zainstaluj**.
::: moniker-end

Można również ręcznie zainstalować dowolne interpretery wymienione w poniższej tabeli poza instalatorem programu Visual Studio. Na przykład jeśli zainstalowano Anaconda 3 przed zainstalowaniem programu Visual Studio, nie trzeba go instalować ponownie za pomocą Instalatora programu Visual Studio. Interpreter można także zainstalować ręcznie, jeśli na przykład nowsza wersja dostępna nie pojawia się jeszcze w Instalatorze programu Visual Studio.

::: moniker range=">=vs-2019"
> [!Note]
> Program Visual Studio obsługuje język Python w wersji 2,7, a także wersję 3,5 i nowszą. Chociaż można użyć programu Visual Studio do edycji kodu pisanego w innych wersjach języka Python, te wersje nie są oficjalnie obsługiwane, a funkcje takie jak IntelliSense i debugowanie mogą nie zadziałać.
::: moniker-end

W przypadku **programu Visual Studio 2015 i jego wcześniejszych wersji**należy ręcznie zainstalować jeden z interpreterów.

Program Visual Studio (wszystkie wersje) automatycznie wykrywa każdy zainstalowany interpreter języka Python i jego środowisko, sprawdzając rejestr zgodnie z [PEP 514 — Rejestracja w języku Python w rejestrze systemu Windows](https://www.python.org/dev/peps/pep-0514/). Instalacje języka Python zwykle znajdują się w obszarze **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-bitowe) i **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-bit), a następnie w węzłach dla dystrybucji, takiej jak **PythonCore** (CPython ) i **ContinuumAnalytics** (Anaconda).

Jeśli program Visual Studio nie wykrywa zainstalowanego środowiska, zobacz [Ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Program Visual Studio Wyświetla wszystkie znane środowiska w oknie [**środowiska języka Python**](managing-python-environments-in-visual-studio.md#the-python-environments-window) i automatycznie wykrywa aktualizacje istniejących interpreterów.

| Interpretera | Opis |
| --- | --- |
| [CPython](https://www.python.org/) | "Natywny" i najczęściej używany interpreter, dostępny w 32-bitowych i 64-bitowych wersjach (zalecane 32-bit). Obejmuje najnowsze funkcje języka, maksymalną zgodność pakietu Python, pełną obsługę debugowania i międzyoperacyjność z [IPython](https://ipython.org/). Zobacz również: [czy należy użyć języka Python 2 lub Python 3?](https://wiki,python.org/moin/Python2orPython3). Należy zauważyć, że program Visual Studio 2015 i jego starsze wersje nie obsługują języka Python 3.6 + i mogą dawać błędy, takie jak **nieobsługiwana wersja języka python 3,6**. Zamiast tego użyj języka Python 3,5 lub starszego. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implementacja platformy .NET w języku Python, dostępna w 32-bitowych i 64-bitowych wersjach, C#zapewniająca/F#/Visual podstawową międzyoperacyjność, dostęp do interfejsów API platformy .NET, C++ standardowe Debugowanie języka Python (ale nie debugowanie w trybieC# mieszanym) oraz mieszane IronPython/debugowanie . IronPython jednak nie obsługuje środowisk wirtualnych. |
| [Anaconda](https://www.continuum.io) | Otwarta platforma analizy danych obsługiwana przez język Python i zawiera najnowszą wersję CPython i większość trudnych do zainstalowania pakietów. Firma Microsoft zaleca, jeśli nie będzie to możliwe. |
| [PyPy](https://www.pypy.org/) | Implementacja JIT śledzenia o wysokiej wydajności w języku Python, która jest przydatna w przypadku długotrwałych programów i sytuacji, w których zidentyfikowano problemy z wydajnością, ale nie można znaleźć innych rozwiązań. Współpracuje z programem Visual Studio, ale z ograniczoną obsługą zaawansowanych funkcji debugowania. |
| [Jython](https://www.jython.org/) | Implementacja języka Python w wirtualna maszyna Java (JVM). Podobnie jak w przypadku IronPython, kod działający w Jython może współdziałać z klasami i bibliotekami Java, ale może nie być w stanie korzystać z wielu bibliotek przeznaczonych dla CPython. Współpracuje z programem Visual Studio, ale z ograniczoną obsługą zaawansowanych funkcji debugowania. |

Deweloperzy, którzy chcą udostępnić nowe formy wykrywania dla środowisk języka Python, zobacz [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (GitHub.com).

## <a name="move-an-interpreter"></a>Przenoszenie interpretera

Jeśli przeniesiesz istniejący interpreter do nowej lokalizacji przy użyciu systemu plików, program Visual Studio nie wykryje zmiany automatycznie.

- Jeśli pierwotnie określono lokalizację interpretera za pomocą okna **środowiska języka Python** , należy edytować jego środowisko przy użyciu karty **Konfiguracja** w tym oknie, aby zidentyfikować nową lokalizację. Zobacz [ręcznie Zidentyfikuj istniejące środowisko](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Jeśli interpreter został zainstalowany przy użyciu programu Instalatora, wykonaj następujące kroki, aby ponownie zainstalować interpreter w nowej lokalizacji:

  1. Przywróć interpreter języka Python do jego oryginalnej lokalizacji.
  2. Odinstaluj interpreter przy użyciu jego Instalatora, który czyści wpisy rejestru.
  3. Zainstaluj ponownie interpreter w odpowiedniej lokalizacji.
  4. Uruchom ponownie program Visual Studio, który powinien automatycznie wykryć nową lokalizację zamiast starej lokalizacji.

Poniższy proces zapewnia, że wpisy rejestru identyfikujące lokalizację interpretera, które są używane przez program Visual Studio, są poprawnie aktualizowane. Korzystanie z Instalatora również obsługuje wszystkie inne efekty uboczne, które mogą istnieć.

## <a name="see-also"></a>Zobacz także

- [Zarządzaj środowiskami języka Python](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Użyj programu Requirements. txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
