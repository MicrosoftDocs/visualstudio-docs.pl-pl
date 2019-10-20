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
ms.openlocfilehash: d72ec4717a7669fd5b4d489b8324f2e0b25c57c0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644703"
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

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)