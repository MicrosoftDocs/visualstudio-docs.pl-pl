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
ms.openlocfilehash: 214897a0f938d8ea52306b8f605948b38f196111
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944965"
---
# <a name="toggle-breakpoint-command"></a>Przełącz punkt przerwania — Polecenie
Włącza punkt przerwania lub wyłączyć, w zależności od bieżącego stanu w bieżącej lokalizacji w pliku.

## <a name="syntax"></a>Składnia

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumenty
 `text` Opcjonalnie. Jeśli tekst jest określona, wiersz jest oznaczona jako nazwany punkt przerwania. W przeciwnym razie wiersz jest oznaczona jako nienazwane punkt przerwania, który przypomina co się stanie, gdy klawisz F9.

## <a name="example"></a>Przykład
 Poniższy przykład zmienia bieżący punkt przerwania.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)