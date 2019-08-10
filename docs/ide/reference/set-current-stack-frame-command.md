---
title: Ustaw bieżącą ramkę stosu — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24880f997d604d3db11ae19a6220c2789da7648f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926074"
---
# <a name="set-current-stack-frame-command"></a>Ustaw bieżącą ramkę stosu — Polecenie
Pozwala ustawić konkretną ramkę stosu.

## <a name="syntax"></a>Składnia

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argumenty
`index`

Wymagana. Wybiera ramkę stosu według jej indeksu.

## <a name="example"></a>Przykład

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)