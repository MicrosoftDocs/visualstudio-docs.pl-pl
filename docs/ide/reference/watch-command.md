---
title: Czujka — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccb87fef9ff91c77c926d5bca40a5e5ec08c3720
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622025"
---
# <a name="watch-command"></a>Czujka — Polecenie
Tworzy i otwiera określone wystąpienie okna **czujka** . Można użyć okna **czujki** do obliczenia wartości zmiennych, wyrażeń i rejestrów, aby edytować te wartości i zapisać wyniki.

## <a name="syntax"></a>Składnia

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumenty

`index`\
Wymagany. Numer wystąpienia okna Czujka.

## <a name="remarks"></a>Uwagi

@No__t_0 musi być liczbą całkowitą. Prawidłowe wartości to 1, 2, 3 lub 4.

## <a name="example"></a>Przykład

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Zobacz też

- [Okna zmiennych automatycznych i zmiennych lokalnych](../../debugger/autos-and-locals-windows.md)
- [Ustaw kontrolkę na zmienne przy użyciu okien czujki i QuickWatch w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)