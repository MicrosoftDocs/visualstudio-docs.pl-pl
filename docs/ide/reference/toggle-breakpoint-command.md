---
title: Przełącz punkt przerwania — Polecenie
description: Dowiedz się, jak użyć polecenia Przełącz punkt przerwania, aby włączyć lub wyłączyć punkt przerwania, w zależności od jego bieżącego stanu w bieżącej lokalizacji w pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0a02cb0659df431b3e6eca7c9ad1f13f8c3676b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886486"
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
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
