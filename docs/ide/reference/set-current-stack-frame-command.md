---
title: Ustaw bieżącą ramkę stosu — Polecenie
description: Zapoznaj się z poleceniem Ustaw bieżącą ramkę stosu i jak można ustawić konkretną ramkę stosu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 032602744247ded5cb38d8a3ae3e1157ccbc5cee
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616606"
---
# <a name="set-current-stack-frame-command"></a>Ustaw bieżącą ramkę stosu — Polecenie
Pozwala ustawić konkretną ramkę stosu.

## <a name="syntax"></a>Składnia

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argumenty
`index`

Wymagane. Wybiera ramkę stosu według jej indeksu.

## <a name="example"></a>Przykład

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)