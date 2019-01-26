---
title: Lista wątków — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 8f4d8706b41448289e5e653ee431ba56fb7d957f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031503"
---
# <a name="list-threads-command"></a>Lista wątków — Polecenie
Wyświetla listę wątków w bieżącym programem.

## <a name="syntax"></a>Składnia

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumenty
 `index`

 Opcjonalna. Wybiera wątku za pomocą jego indeksu do bieżącego wątku.

## <a name="remarks"></a>Uwagi
 Jeśli zostanie określony, `index` argument oznacza wskazany wątek jako bieżącego wątku. Znak gwiazdki (*) jest wyświetlana na liście obok bieżącego wątku.

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