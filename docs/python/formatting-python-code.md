---
title: Formatowanie kodu języka Python
description: Visual Studio może automatycznie formatować kod języka Python, w tym odstępy, instrukcje, zawijanie i komentarze.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957541"
---
# <a name="format-python-code"></a>Formatowanie kodu języka Python

Program Visual Studio umożliwia szybkie formatowanie kodu w celu dopasowania do wstępnie skonfigurowanych opcji formatowania.

- Aby sformatować zaznaczenie, wybierz **pozycję Edytuj** > **zaznaczenie formatu** **zaawansowanego** > lub naciśnij **klawisze Ctrl**+**E** > **F**.
- Aby sformatować cały plik: wybierz **pozycję Edytuj** > **dokument formatu** **zaawansowanego** > lub naciśnij **klawisze Ctrl**+**E** > **D**.

Opcje są ustawiane za pomocą**opcji** >  **Narzędzia** > **Edytor** > tekstu**Formatowanie** **języka Python** > i jego zagnieżdżone karty. Aby wyświetlić te opcje, musisz wybrać opcję **Pokaż wszystkie ustawienia:**

![Opcje formatowania języka Python w programie Visual Studio](media/options-editor-formatting.png)

Domyślnie opcje formatowania są ustawione tak, aby odpowiadało nadzbiorowi [przewodnika po stylu PEP 8](https://www.python.org/dev/peps/pep-0008/). Karta **Ogólne** określa, kiedy stosowane jest formatowanie; ustawienia pozostałych trzech kart są opisane w tym artykule.

[Obsługa języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md) dodaje również przydatne polecenie [**Wypełnij komentarz akapit**](#fill-comment-paragraph-command) do menu **Edytuj** > **zaawansowane,** zgodnie z opisem w dalszej sekcji.

## <a name="spacing"></a>Odstępy

Kontrolki **odstępów,** w których spacje są wstawiane lub usuwane wokół różnych konstrukcji językowych. Każda opcja ma trzy możliwe wartości:

- Zaznaczone: zapewnia zastosowanie odstępów.
- Wyczyszczone: usuwa wszelkie odstępy.
- Nieokreślony: pozostawia oryginalne formatowanie na swoim miejscu.

Przykłady dla różnych opcji znajdują się w następujących tabelach:

| Opcja definicje klas | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| **Wstawianie odstępu między listą nazw i baz deklaracji klasy** | `class X (object): pass` | `class X(object): pass` |
| **Wstawianie spacji w nawiasach listy baz** | `class X( object ): pass` | `class X(object): pass` |
| **Wstawianie spacji w nawiasach listy pustych baz** | `class X( ): pass` | `class X(): pass` |

<br/>

| Opcja Definicje funkcji | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| **Wstawianie odstępu między nazwą deklaracji funkcji a listą parametrów** | `def X (): pass` | `def X(): pass` |
| **Wstawianie spacji w nawiasach listy parametrów** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Wstawianie miejsca w nawiasach listy pustych parametrów** | `def X( ): pass` | `def X(): pass` |
| **Wstawianie spacji wokół '=' w domyślnych wartościach parametrów** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Wstawianie spacji przed i po zwracaniu operatorów adnotacji** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opcja Operatorzy | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| **Wstawianie spacji wokół operatorów binarnych** | `a + b` | `a+b` |
| **Wstawianie spacji wokół przydziałów** | `a = b` | `a=b` |

<br/>

| Opcja odstępów między wyrażeniami | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| **Wstawianie odstępu między nazwą i listą argumentów wywołania funkcji** | `X ()` | `X()` |
| **Wstawianie miejsca w nawiasach pustej listy argumentów** | `X( )` | `X()` |
| **Wstawianie spacji w nawiasach listy argumentów** | `X( a, b )` | `X(a, b)` |
| **Wstawianie spacji w nawiasach wyrażenia** | `( a )` | `(a)` |
| **Wstawianie miejsca w pustych nawiasach krotki** | `( )` | `()` |
| **Wstawianie spacji w nawiasach krotki** | `( a, b )` | `(a, b)` |
| **Wstawianie miejsca w pustych nawiasach kwadratowych** | `[ ]` | `[]` |
| **Wstawianie spacji w nawiasach kwadratowych list** | `[ a, b ]` | `[a, b]` |
| **Wstawianie miejsca przed otwartym kwadratowym nawiasem** | `x [i]` | `x[i]` |
| **Wstawianie przestrzeni w nawiasach kwadratowych** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instrukcje

Opcje **instrukcji** kontrolować automatyczne przepisywanie różnych instrukcji w więcej form Pythonic.

| Opcja | Przed formatowaniem | Po sformatowaniu |
| --- | --- | --- |
| **Umieszczanie importowanych modułów w nowym wierszu** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Usuń niepotrzebne średniki** | `x = 42;` | `x = 42` |
| **Umieszczanie wielu instrukcji w nowych wierszach** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Zawijania

**Zawijanie** umożliwia ustawienie **maksymalnej szerokości komentarza** (domyślnie jest to 80). Jeśli **Wrap komentarze, które są zbyt szerokie** opcja jest ustawiona, Visual Studio formatuje komentarze, aby nie przekraczać tej maksymalnej szerokości.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Polecenie Wypełnij akapit komentarza

**Edytuj** > **zaawansowaną** > **akapit komentarza do wypełnienia** **(Ctrl**+**E** > **P)** ponownie wlacza i formatuje tekst komentarza, łącząc krótkie wiersze i rozbijając długie.

Przykład:

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
