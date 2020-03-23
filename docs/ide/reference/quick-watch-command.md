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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565633"
---
# <a name="quick-watch-command"></a>Szybka czujka — Polecenie
Wyświetla zaznaczony lub określony tekst w polu Wyrażenie w oknie [QuickWatch.](../../debugger/watch-and-quickwatch-windows.md) To okno dialogowe służy do obliczania bieżącej wartości zmiennej lub wyrażenia rozpoznawanej przez debuger lub zawartości rejestru. Ponadto można zmienić wartość dowolnej zmiennej niekonserwowej lub zawartości dowolnego rejestru.

## <a name="syntax"></a>Składnia

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumenty

`text`\
Element opcjonalny. Tekst do dodania do okna dialogowego **QuickWatch.**

## <a name="remarks"></a>Uwagi

Jeśli `text` zostanie pominięty, aktualnie zaznaczony tekst lub wyraz na kursorze zostanie dodany do okna Czujka.

## <a name="example"></a>Przykład

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Zobacz też

- [Ustawianie zegarka na zmiennych przy użyciu systemu Watch i QuickWatch Windows w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
