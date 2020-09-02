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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1b36b8f4d9970d94eb83c47b59e85d01f932589
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595491"
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
Gdy jest określony, `index` argument oznacza wskazany wątek jako bieżący wątek. Gwiazdka (*) jest wyświetlana na liście obok bieżącego wątku.

## <a name="example"></a>Przykład

```
>Debug.ListThreads
```

## <a name="see-also"></a>Zobacz też

- [Listing stosu wywołań — polecenie](../../ide/reference/list-call-stack-command.md)
- [List demontażu — polecenie](../../ide/reference/list-disassembly-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
