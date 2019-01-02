---
title: Czujka — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccc9c6af2a87502c2b651e91f7d935ffc7ae3474
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964484"
---
# <a name="watch-command"></a>Czujka — Polecenie
Tworzy i otwiera określone wystąpienie **Obejrzyj** okna. Możesz użyć **Obejrzyj** okna do obliczania wartości zmiennych, wyrażenia i rejestry, aby edytować te wartości i zapisać wyniki.

## <a name="syntax"></a>Składnia

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumenty
 `index`

 Wymagana. Liczba wystąpień okna czujki.

## <a name="remarks"></a>Uwagi
 `index` Musi być liczbą całkowitą. Prawidłowe wartości to 1, 2, 3 lub 4.

## <a name="example"></a>Przykład

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Zobacz też

- [Okna zmiennych automatycznych i zmiennych lokalnych](../../debugger/autos-and-locals-windows.md)
- [Ustawianie wyrażenia kontrolnego na zmiennych przy użyciu wyrażenie kontrolne i QuickWatch Windows w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)