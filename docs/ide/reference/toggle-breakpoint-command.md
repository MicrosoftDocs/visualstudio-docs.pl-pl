---
title: Przełącz punkt przerwania — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8294c25bcf3b62f9d6480e170d4693a9be85079
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748575"
---
# <a name="toggle-breakpoint-command"></a>Przełącz punkt przerwania — Polecenie
Włącza lub wyłącza punkt przerwania w zależności od bieżącego stanu w bieżącej lokalizacji pliku.

## <a name="syntax"></a>Składnia

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumenty

`text`\
Opcjonalny. Jeśli tekst jest określony, linia jest oznaczona jako nazwany punkt przerwania. W przeciwnym razie wiersz jest oznaczony jako nienazwany punkt przerwania, który jest podobny do tego, co się dzieje po naciśnięciu klawisza F9.

## <a name="example"></a>Przykład
Poniższy przykład przełącza bieżący punkt przerwania.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)