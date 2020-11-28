---
title: Debuguj. Print
description: Dowiedz się więcej na temat polecenia Print i sposobu szacowania wyrażenia lub wyświetlania określonego tekstu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0524ce015ea4675254615c11e5768e59049c37f6
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304133"
---
# <a name="print-command"></a>Print — Polecenie

Oblicza wyrażenie lub Wyświetla określony tekst.

## <a name="syntax"></a>Składnia

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumenty

`text`

Wymagane. Wyrażenie, które ma zostać obliczone lub tekst do wyświetlenia.

## <a name="remarks"></a>Uwagi

Możesz użyć znaku zapytania (?) jako aliasu dla tego polecenia. Tak więc, na przykład, polecenie

```cmd
>Debug.Print expA
```

można również napisać jako

```cmd
? expA
```

Obie wersje tego polecenia zwracają bieżącą wartość wyrażenia `expA` .

## <a name="example"></a>Przykład

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Zobacz także

- [Polecenie szacowania instrukcji](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
