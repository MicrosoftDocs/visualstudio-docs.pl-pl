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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f6382a79884bf8c3891a3a191b594bf183efb62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565633"
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
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
