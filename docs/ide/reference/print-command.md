---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df609011250cebc097d3d356242302dbe41f8007
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56953560"
---
# <a name="print-command"></a>Print — Polecenie

Oblicza wyrażenie lub wyświetla określony tekst.

## <a name="syntax"></a>Składnia

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumenty

`text`

Wymagana. Wyrażenie do oceny lub tekst do wyświetlenia.

## <a name="remarks"></a>Uwagi

Dla tego polecenia, można użyć znaku zapytania (?) jako alias. Tak na przykład polecenie

```cmd
>Debug.Print expA
```

można również zapisać jako

```cmd
? expA
```

Obie wersje to polecenie zwraca bieżącą wartość wyrażenia `expA`.

## <a name="example"></a>Przykład

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Zobacz też

- [Oceń instrukcję, polecenie](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)