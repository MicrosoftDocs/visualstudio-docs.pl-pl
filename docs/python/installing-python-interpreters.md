---
title: Wybieranie i instalowanie interpreterów języka Python
description: Pełna lista interpreterów języka Python obsługiwanych w programie Visual Studio z krótkimi instrukcjami dotyczącymi tego, gdzie można znaleźć ich instalatory.
ms.date: 06/05/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8070bb93a1dd76ad29832afae15d83788300ae7a
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2021
ms.locfileid: "107941113"
---
# <a name="install-python-interpreters"></a>Instalowanie interpreterów języka Python

Domyślnie instalowanie obciążenia programowania w języku Python w wersji Visual Studio 2017 i nowszych również instaluje język Python 3 (wersja 64-bitowa). Opcjonalnie możesz zainstalować 32-bitowe i 64-bitowe wersje języka Python 2 i Python 3 wraz z programem Miniconda (Visual Studio 2019) lub Anaconda 2/Anaconda 3 (Visual Studio 2017), zgodnie z opisem w [tece Instalacja](installing-python-support-in-visual-studio.md).

::: moniker range=">=vs-2019"
Alternatywnie możesz zainstalować standardowe interpretery języka Python w **oknie dialogowym Dodawanie środowiska.** Wybierz polecenie **Dodaj środowisko** w oknie Środowiska **języka Python** lub na pasku narzędzi języka Python, wybierz kartę instalacji języka **Python,** wskaż interpretery do zainstalowania, a następnie wybierz **pozycję Zainstaluj**.
::: moniker-end

Możesz również ręcznie zainstalować dowolny interpreter wymieniony w poniższej tabeli poza instalatorem Visual Studio instalatora. Jeśli na przykład program Anaconda 3 został zainstalowany przed zainstalowaniem programu Visual Studio, nie trzeba instalować go ponownie za pośrednictwem instalatora Visual Studio instalacji. Interpreter można również zainstalować ręcznie, jeśli na przykład jest dostępna nowsza wersja, która nie jest jeszcze wyświetlana w Visual Studio instalatorze.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio obsługuje język Python w wersji 2.7, a także wersje od 3.5 do 3.7. Chociaż istnieje możliwość edytowania kodu napisanego Visual Studio innych wersjach języka Python, te wersje nie są oficjalnie obsługiwane, a funkcje, takie jak IntelliSense i debugowanie, mogą nie działać.
::: moniker-end

W **Visual Studio 2015** r. i starszych należy ręcznie zainstalować jeden z interpreterów.

Visual Studio (wszystkie wersje) automatycznie wykrywa każdy zainstalowany interpreter języka Python i jego środowisko, sprawdzając rejestr zgodnie z [rejestracją PEP 514](https://www.python.org/dev/peps/pep-0514/)— Python w rejestrze systemu Windows. Instalacje języka Python są zwykle dostępne w środowiskach **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-bitowych) iHKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python(64-bitowych), **a** następnie w węzłach dystrybucji, takich jak **PythonCore** (CPython) i **ContinuumAnalytics** (Anaconda).

Jeśli Visual Studio nie wykryje zainstalowanego środowiska, zobacz [Ręczne identyfikowanie istniejącego środowiska.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

Visual Studio wszystkie znane środowiska w oknie Środowiska [**języka Python**](managing-python-environments-in-visual-studio.md#the-python-environments-window) i automatycznie wykrywa aktualizacje istniejących interpreterów.

| Interpreter | Opis |
| --- | --- |
| [CPython](https://www.python.org/) | "Natywny" i najczęściej używany interpreter, dostępny w wersjach 32-bitowych i 64-bitowych (zalecane 32-bitowe). Obejmuje najnowsze funkcje językowe, maksymalną zgodność pakietów języka Python, pełną obsługę debugowania i międzyoptykę z [językiem IPython.](https://ipython.org/) Zobacz też: [Czy należy używać języka Python 2 lub Python 3?](https://wiki.python.org/moin/Python2orPython3). Pamiętaj, że Visual Studio 2015 i starsze nie obsługują języka Python w wersji 3.6 lub starszej i mogą dawać błędy, takie jak Nieobsługiwany język Python w **wersji 3.6.** Zamiast tego użyj języka Python w wersji 3.5 lub starszej. |
| [Boo](https://github.com/IronLanguages/ironpython2) | Implementacja języka Python na platformie .NET, dostępna w wersjach 32-bitowych i 64-bitowych, zapewniająca międzyoptykę języka C#/F#/Visual Basic, dostęp do interfejsów API .NET, standardowe debugowanie języka Python (ale nie debugowanie w trybie mieszanym języka C++) i debugowanie mieszane IronPython/C#. IronPython nie obsługuje jednak środowisk wirtualnych. |
| [Anaconda](https://www.continuum.io) | Otwarta platforma nauki o danych wspierana przez język Python, która zawiera najnowszą wersję środowiska CPython i większość trudnych do zainstalowania pakietów. Jeśli w przeciwnym razie nie możesz podjąć innej decyzji, zalecamy jej skorzystanie. |
| [PyPy](https://www.pypy.org/) | Implementacja JIT śledzenia o wysokiej wydajności języka Python, która jest dobra dla długotrwałych programów i sytuacji, w których można zidentyfikować problemy z wydajnością, ale nie można znaleźć innych rozdzielczości. Działa z Visual Studio ale z ograniczoną obsługą zaawansowanych funkcji debugowania. |
| [Jython](https://www.jython.org/) | Implementacja języka Python na wirtualna maszyna Java (JVM). Podobnie jak w przypadku aplikacji IronPython, kod uruchomiony w języku Jython może współdziałać z klasami i bibliotekami języka Java, ale może nie być w stanie używać wielu bibliotek przeznaczonych dla języka CPython. Działa z Visual Studio ale z ograniczoną obsługą zaawansowanych funkcji debugowania. |

Deweloperzy, którzy chcą zapewnić nowe formy wykrywania dla środowisk Python, zobacz Wykrywanie środowiska [PTVS](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## <a name="move-an-interpreter"></a>Przenoszenie interpretera

Jeśli przeniesiesz istniejący interpreter do nowej lokalizacji przy użyciu systemu plików, Visual Studio nie wykryje zmiany automatycznie.

- Jeśli pierwotnie określono lokalizację interpretera za pośrednictwem okna Środowiska  **Python,** edytuj jego środowisko przy użyciu karty Konfigurowanie w tym oknie, aby zidentyfikować nową lokalizację. Zobacz [Ręczne identyfikowanie istniejącego środowiska.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

- Jeśli interpreter został zainstalowany przy użyciu programu instalacyjnego, należy wykonać następujące kroki, aby ponownie zainstalować interpreter w nowej lokalizacji:

  1. Przywróć interpreter języka Python do oryginalnej lokalizacji.
  2. Odinstaluj interpreter przy użyciu jego instalatora, który wyczyści wpisy rejestru.
  3. Zainstaluj ponownie interpreter w żądanej lokalizacji.
  4. Uruchom Visual Studio, co powinno automatycznie wykryć nową lokalizację w miejsce starej lokalizacji.

Ten proces gwarantuje, że wpisy rejestru, które identyfikują lokalizację interpretera, która Visual Studio, są prawidłowo aktualizowane. Użycie instalatora obsługuje również wszelkie inne efekty uboczne, które mogą istnieć.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie środowiskami języka Python](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie requirements.txt zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Informacje o oknach środowisk Python](python-environments-window-tab-reference.md)
