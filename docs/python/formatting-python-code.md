---
title: Formatowanie kodu w języku Python
description: Program Visual Studio można automatycznie ponownie sformatować kodu języka Python, w tym odstępy, instrukcji, zawijania i komentarze.
ms.date: 02/11/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 46aba6fc0af8fa5c89f8d919fac17f7b59f7c2a2
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987499"
---
# <a name="format-python-code"></a>Formatowanie kodu w języku Python

Program Visual Studio pozwala w szybko Formatuj ponownie kod, aby dopasować wstępnie skonfigurowanych opcji formatowania.

- Na formatowanie zaznaczenia: Wybierz **Edytuj** > **zaawansowane** > **Formatuj zaznaczenie** lub naciśnij **Ctrl** + **E** > **F**.
- Aby sformatować całego pliku: Wybierz **Edytuj** > **zaawansowane** > **dokumentu w formacie** lub naciśnij **Ctrl** + **E** > **D**.

Opcje są ustawiane za pomocą **narzędzia** > **opcje** > **edytora tekstów** > **Python**  >  **Formatowanie** i jego zagnieżdżonych karty. Musisz wybrać **Pokaż wszystkie ustawienia** opcje te są wyświetlane:

![Opcje w programie Visual Studio formatowania języka Python](media/options-editor-formatting.png)

Opcje formatowania, które domyślnie są ustawione na zgodny nadzbiorem [8 program ten przewodnik stylistyczny](https://www.python.org/dev/peps/pep-0008/). **Ogólne** kartę Określa, kiedy stosowane to formatowanie; ustawienia dla trzech kartach są opisane w tym artykule.

[Obsługa języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md) dodaje również przydatne [ **wypełnienia akapitu komentarz** ](#fill-comment-paragraph-command) polecenia do **Edytuj**  >   **Zaawansowane** menu, zgodnie z opisem w dalszej części tego tematu.

## <a name="spacing"></a>Odstępy

**Odstępy** formantów, gdzie miejsca do magazynowania są wstawiane i usuwane wokół różnych konstrukcji językowych. Każda opcja ma trzy możliwe wartości:

- Zaznaczone: zapewnia, że zastosowano odstępy.
- Wyczyszczone: usuwa wszelkie odstępy.
- Nieokreślony: pozostawia oryginalne formatowanie w miejscu.

Przykłady dla różnych opcji znajdują się w poniższych tabelach:

| Opcja definicji klasy | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| **Wstaw spację między nazwę deklarację klasy i lista baz** | `class X (object): pass` | `class X(object): pass` |
| **Wstaw spację wewnątrz nawiasów listy zasad** | `class X( object ): pass` | `class X(object): pass` |
| **Wstaw spację wewnątrz nawiasów listy podstaw pusty** | `class X( ): pass` | `class X(): pass` |

<br/>

| Definicje funkcji-opcja | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| **Wstaw spację między nazwę deklarację funkcji i listy parametrów** | `def X (): pass` | `def X(): pass` |
| **Wstaw spację wewnątrz nawiasów listy parametrów** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Wstaw spację wewnątrz nawiasów listy parametrów empty** | `def X( ): pass` | `def X(): pass` |
| **Wstawiaj odstępy dookoła "=" w wartości domyślne parametrów** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Wstaw spację przed i po operatorach adnotacji zwracanego** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opcja operatorów | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| **Wstawiaj odstępy dookoła operatorów dwuargumentowych** | `a + b` | `a+b` |
| **Wstawiaj odstępy dookoła przypisania** | `a = b` | `a=b` |

<br/>

| Opcję odstępy dla wyrażeń | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| **Wstaw spację między nazwę wywołania funkcji i listą argumentów** | `X ()` | `X()` |
| **Wstaw spację wewnątrz nawiasów listy pusty argument** | `X( )` | `X()` |
| **Wstaw spację wewnątrz nawiasów listy argumentów** | `X( a, b )` | `X(a, b)` |
| **Wstaw spację wewnątrz nawiasów wyrażeń** | `( a )` | `(a)` |
| **Wstaw spację wewnątrz nawiasów puste krotki** | `( )` | `()` |
| **Wstaw spację wewnątrz nawiasów krotki** | `( a, b )` | `(a, b)` |
| **Wstaw spację wewnątrz pustymi nawiasami kwadratowymi** | `[ ]` | `[]` |
| **Wstaw spacje wewnątrz nawiasów kwadratowych list** | `[ a, b ]` | `[a, b]` |
| **Wstaw odstęp przed nawiasem kwadratowym** | `x [i]` | `x[i]` |
| **Wstaw spację wewnątrz nawiasów kwadratowych** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instrukcje

**Instrukcji** opcje umożliwiają kontrolowanie automatyczne ponowne napisanie różne instrukcje w formularzach Pythonic więcej.

| Opcja | Przed formatowaniem | Po sformatowaniu |
| --- | --- | --- |
| **Umieść zaimportowanych modułów w nowym wierszu** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Usuń niepotrzebne średnikami** | `x = 42;` | `x = 42` |
| **Umieść użycie wielu instrukcji w nowych wierszach** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Zawijanie

**Zawijanie** pozwala ustawić **maksymalna szerokość komentarz** (wartość domyślna to 80). Jeśli **opakować komentarze, które są zbyt szerokie** wyboru jest zaznaczone, komentarze, aby nie przekroczyć tej maksymalną szerokość formatowane w programie Visual Studio.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Wprowadź polecenie Akapit komentarz

**Edytuj** > **zaawansowane** > **wprowadź komentarz akapitu** (**Ctrl**+**E**  >  **P**) i który formatuje tekst komentarza, łączenie ze sobą krótkich wierszy i podzielenie długie z nich.

Na przykład:

```python
# foo
# bar
# baz
```

zmiany:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

zmiany:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
