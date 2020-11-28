---
title: Szybka czujka — Polecenie
description: Dowiedz się więcej o poleceniu szybkiej czujki i sposobie wyświetlania zaznaczonego lub określonego tekstu w polu wyrażenie okna QuickWatch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6185418364e8b22e1f473308b2db9899c8778d13
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304164"
---
# <a name="quick-watch-command"></a>Szybka czujka — Polecenie
Wyświetla wybrany lub określony tekst w polu wyrażenie okna [QuickWatch](../../debugger/watch-and-quickwatch-windows.md) . Za pomocą tego okna dialogowego można obliczyć bieżącą wartość zmiennej lub wyrażenia rozpoznawanego przez debuger lub zawartość rejestru. Ponadto można zmienić wartość dowolnej zmiennej innej niż stała lub zawartości dowolnego rejestru.

## <a name="syntax"></a>Składnia

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumenty

`text`\
Opcjonalny. Tekst, który ma zostać dodany do okna dialogowego **QuickWatch** .

## <a name="remarks"></a>Uwagi

Jeśli `text` zostanie pominięty, aktualnie zaznaczony tekst lub słowo w kursorze zostanie dodane do okno wyrażeń kontrolnych.

## <a name="example"></a>Przykład

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Zobacz także

- [Ustaw kontrolkę na zmienne przy użyciu okien czujki i QuickWatch w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
