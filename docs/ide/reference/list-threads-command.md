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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b3ad3b30329d574145ce7de839a3e6c164df2d5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919082"
---
# <a name="list-threads-command"></a>Lista wątków — Polecenie
Wyświetla listę wątków w bieżącym programem.

## <a name="syntax"></a>Składnia

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumenty
`index`

Opcjonalny. Wybiera wątek według indeksu, który będzie bieżącym wątkiem.

## <a name="remarks"></a>Uwagi
Gdy jest `index` określony, argument oznacza wskazany wątek jako bieżący wątek. Gwiazdka (*) jest wyświetlana na liście obok bieżącego wątku.

## <a name="example"></a>Przykład

```
>Debug.ListThreads
```

## <a name="see-also"></a>Zobacz też

- [Lista stosu wywołań, polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista dezasemblacji, polecenie](../../ide/reference/list-disassembly-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)