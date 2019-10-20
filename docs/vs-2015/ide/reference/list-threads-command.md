---
title: Lista wątków — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671140"
---
# <a name="list-threads-command"></a>Lista wątków — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla listę wątków w bieżącym programie.

## <a name="syntax"></a>Składnia

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumenty
 `index` opcjonalny. Wybiera wątek według indeksu, który będzie bieżącym wątkiem.

## <a name="remarks"></a>Uwagi
 Gdy jest określony, argument `index` oznacza wskazany wątek jako bieżący wątek. Gwiazdka (*) jest wyświetlana na liście obok bieżącego wątku.

## <a name="example"></a>Przykład

```
>Debug.ListThreads
```

## <a name="see-also"></a>Zobacz też
 [Lista poleceń stosu wywołań](../../ide/reference/list-call-stack-command.md) poleceń polecenia [demontażu polecenie](../../ide/reference/list-disassembly-command.md) [Visual Studio](../../ide/reference/visual-studio-commands.md) Commands [window](../../ide/reference/command-window.md) [Find/Command Box](../../ide/find-command-box.md) [program Visual Studio Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
