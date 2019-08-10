---
title: Szybka czujka — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75afe1cdd0d1755d2953e6b9e6e3e85a089b3303
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926125"
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

## <a name="see-also"></a>Zobacz też

- [Ustaw kontrolkę na zmienne przy użyciu okien czujki i QuickWatch w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)