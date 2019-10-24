---
title: Lista wątków — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c89f4e38d21e7dd66f53b8e768019a3e53c7a39
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747886"
---
# <a name="list-threads-command"></a>Lista wątków — Polecenie
Wyświetla listę wątków w bieżącym programie.

## <a name="syntax"></a>Składnia

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumenty
`index`

Opcjonalny. Wybiera wątek według indeksu, który będzie bieżącym wątkiem.

## <a name="remarks"></a>Uwagi
Gdy jest określony, argument `index` oznacza wskazany wątek jako bieżący wątek. Gwiazdka (*) jest wyświetlana na liście obok bieżącego wątku.

## <a name="example"></a>Przykład

```
>Debug.ListThreads
```

## <a name="see-also"></a>Zobacz także

- [Lista stosu wywołań, polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista dezasemblacji, polecenie](../../ide/reference/list-disassembly-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)