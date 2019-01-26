---
title: Szybka czujka — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 0dcfd4e7245699be6bdadc4a43ceacbf7a718e43
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921794"
---
# <a name="quick-watch-command"></a>Szybka czujka — Polecenie
Wyświetla zaznaczony lub określony tekst w polu wyrażenie [QuickWatch](../../debugger/watch-and-quickwatch-windows.md) okna. To okno dialogowe służy do obliczania wartości bieżącej zmiennej lub wyrażenia uznane przez debuger lub zawartości rejestru. Ponadto można zmienić wartość dowolnej zmiennej niestały lub zawartość dowolnego rejestru.

## <a name="syntax"></a>Składnia

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumenty
 `text`

 Opcjonalna. Tekst do dodania do **QuickWatch** okno dialogowe.

## <a name="remarks"></a>Uwagi
 Jeśli `text` jest pominięty, aktualnie zaznaczonego tekstu lub word przy kursorze jest dodawany do okna czujki.

## <a name="example"></a>Przykład

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Zobacz też

- [Ustawianie wyrażenia kontrolnego na zmiennych przy użyciu wyrażenie kontrolne i QuickWatch Windows w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)