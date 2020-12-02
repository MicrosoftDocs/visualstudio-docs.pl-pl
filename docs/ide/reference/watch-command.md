---
title: Czujka — Polecenie
description: Dowiedz się więcej na temat polecenia Watch i sposobu tworzenia i otwierania określonego wystąpienia okno wyrażeń kontrolnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631c9cf61e6da70b3c7554a1aac0cacc8eef0294
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480151"
---
# <a name="watch-command"></a>Czujka — Polecenie
Tworzy i otwiera określone wystąpienie okna **czujka** . Można użyć okna **czujki** do obliczenia wartości zmiennych, wyrażeń i rejestrów, aby edytować te wartości i zapisać wyniki.

## <a name="syntax"></a>Składnia

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumenty

`index`\
Wymagane. Numer wystąpienia okna Czujka.

## <a name="remarks"></a>Uwagi

Wartość `index` musi być liczbą całkowitą. Prawidłowe wartości to 1, 2, 3 lub 4.

## <a name="example"></a>Przykład

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Zobacz także

- [Okna zmiennych automatycznych i zmiennych lokalnych](../../debugger/autos-and-locals-windows.md)
- [Ustaw kontrolkę na zmienne przy użyciu okien czujki i QuickWatch w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
