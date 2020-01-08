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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
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

W przypadku pominięcia `text`, w okno wyrażeń kontrolnych zostanie dodany aktualnie zaznaczony tekst lub słowo.

## <a name="example"></a>Przykład

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Zobacz także

- [Ustaw kontrolkę na zmienne przy użyciu okien czujki i QuickWatch w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
