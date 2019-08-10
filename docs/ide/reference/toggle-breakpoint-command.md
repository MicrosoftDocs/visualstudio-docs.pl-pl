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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18473fbd8ee0f7c4b415880da61c86de0bae6fc5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925976"
---
# <a name="toggle-breakpoint-command"></a>Przełącz punkt przerwania — Polecenie
Włącza punkt przerwania lub wyłączyć, w zależności od bieżącego stanu w bieżącej lokalizacji w pliku.

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