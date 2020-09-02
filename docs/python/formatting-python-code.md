---
title: Formatowanie kodu w języku Python
description: Program Visual Studio może automatycznie ponownie formatować kod w języku Python, w tym odstępy, instrukcje, zawijanie i komentarze.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e95d05c3fbc0dd46d235c7480bd4a9caa48947e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62957541"
---
# <a name="format-python-code"></a>Formatowanie kodu w języku Python

Program Visual Studio pozwala szybko ponownie sformatować kod, aby dopasować wstępnie skonfigurowane opcje formatowania.

- Aby sformatować zaznaczenie: wybierz opcję **Edytuj**  >  **Zaawansowany**  >  **Format zaznacz** lub naciśnij **klawisze CTRL** + **E**  >  **F**.
- Aby sformatować cały plik: wybierz opcję **Edytuj**  >  dokument w formacie**zaawansowanym**  >  **Format Document** lub naciśnij **klawisze CTRL** + **E**  >  **D**.

Opcje są ustawiane za poorednictwem opcji **Narzędzia**  >  **Options**  >  **Edytor tekstu**  >  w języku**Python**  >  **Formatting** i na kartach zagnieżdżonych. Musisz wybrać opcję **Pokaż wszystkie ustawienia** dla następujących opcji:

![Opcje formatowania języka Python w programie Visual Studio](media/options-editor-formatting.png)

Opcje formatowania domyślnie są ustawione jako zgodne z nadzbiorem [stylu PEP 8](https://www.python.org/dev/peps/pep-0008/). Karta **Ogólne** określa, kiedy jest stosowane formatowanie; w tym artykule opisano ustawienia dla pozostałych trzech kart.

[Obsługa języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md) dodaje także przydatne polecenie [**wypełnienia akapitu**](#fill-comment-paragraph-command) do menu **Edytuj**  >  **Zaawansowane** zgodnie z opisem w dalszej części.

## <a name="spacing"></a>Odstępy

**Odstępy** , w których są wstawiane lub usuwane spacje wokół różnych konstrukcji językowych. Każda opcja ma trzy możliwe wartości:

- Zaznaczone: zapewnia, że odstępy są stosowane.
- Wyczyszczone: usuwa wszystkie odstępy.
- Nieokreślone: pozostawia oryginalne formatowanie na miejscu.

Przykłady dla różnych opcji podano w następujących tabelach:

| Opcja definicji klas | Zaznaczono | Zaznaczenia |
| --- | --- | --- |
| **Wstaw spację między nazwą deklaracji klasy a listą baz danych** | `class X (object): pass` | `class X(object): pass` |
| **Wstaw spację wewnątrz nawiasów listy baz** | `class X( object ): pass` | `class X(object): pass` |
| **Wstaw spację wewnątrz pustych nawiasów listy baz** | `class X( ): pass` | `class X(): pass` |

<br/>

| Opcja definicji funkcji | Zaznaczono | Zaznaczenia |
| --- | --- | --- |
| **Wstaw spację między nazwą a listą parametrów deklaracji funkcji** | `def X (): pass` | `def X(): pass` |
| **Wstaw spację wewnątrz nawiasów listy parametrów** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Wstaw spację wewnątrz pustych nawiasów listy parametrów** | `def X( ): pass` | `def X(): pass` |
| **Wstaw spacje wokół instrukcji "=" w domyślnych wartościach parametrów** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Wstaw spację przed operatorem adnotacji Return i po nim** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opcja operatorów | Zaznaczono | Zaznaczenia |
| --- | --- | --- |
| **Wstaw odstępy dookoła operatorów binarnych** | `a + b` | `a+b` |
| **Wstaw spacje wokół przypisań** | `a = b` | `a=b` |

<br/>

| Opcja odstępu wyrażenia | Zaznaczono | Zaznaczenia |
| --- | --- | --- |
| **Wstaw spację między nazwą wywołania funkcji a listą argumentów** | `X ()` | `X()` |
| **Wstaw spację wewnątrz nawiasów listy pustych argumentów** | `X( )` | `X()` |
| **Wstaw spację wewnątrz nawiasów listy argumentów** | `X( a, b )` | `X(a, b)` |
| **Wstaw spację wewnątrz nawiasów wyrażenia** | `( a )` | `(a)` |
| **Wstaw spację w nawiasach pustej kolekcji** | `( )` | `()` |
| **Wstaw spację wewnątrz nawiasów krotek** | `( a, b )` | `(a, b)` |
| **Wstaw spację wewnątrz pustych nawiasów kwadratowych** | `[ ]` | `[]` |
| **Wstaw spacje w nawiasach kwadratowych list** | `[ a, b ]` | `[a, b]` |
| **Wstaw spację przed otwierającym nawiasem kwadratowym** | `x [i]` | `x[i]` |
| **Wstaw spację wewnątrz nawiasów kwadratowych** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instrukcje

Opcje **instrukcji** kontrolują automatyczne ponowne zapisywanie różnych instrukcji w większej liczbie formularzy Python.

| Opcja | Przed formatowaniem | Po formatowaniu |
| --- | --- | --- |
| **Umieść zaimportowane moduły w nowym wierszu** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Usuń niepotrzebne średniki** | `x = 42;` | `x = 42` |
| **Umieść wiele instrukcji w nowych wierszach** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Opakowującego

Funkcja **zawijania** umożliwia ustawienie **maksymalnej szerokości komentarza** (wartość domyślna to 80). Jeśli ustawiono opcję **Zawijaj komentarze, które są zbyt szerokie** , program Visual Studio ponownie sformatuje komentarze, aby nie przekroczyć tej maksymalnej szerokości.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Wypełnienie akapitu komentarza — polecenie

**Edytuj**  >  **Zaawansowane**  >  **Wypełnienie komentarza akapitu** (**Ctrl** + **E**  >  **P**) powoduje przepełnienie i sformatowanie tekstu komentarza, połączenie krótkich wierszy i rozdzielenie długich.

Na przykład:

```python
# foo
# bar
# baz
```

zmiany w:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

zmiany w:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
