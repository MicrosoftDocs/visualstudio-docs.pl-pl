---
title: Debug.Drukuj
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
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567843"
---
# <a name="print-command"></a>Print — Polecenie

Oblicza wyrażenie lub wyświetla określony tekst.

## <a name="syntax"></a>Składnia

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumenty

`text`

Wymagany. Wyrażenie do oceny lub tekst do wyświetlenia.

## <a name="remarks"></a>Uwagi

Jako alias tego polecenia można użyć znaku zapytania (?). Tak więc, na przykład, polecenie

```cmd
>Debug.Print expA
```

można również zapisać jako

```cmd
? expA
```

Obie wersje tego polecenia zwracają bieżącą `expA`wartość wyrażenia .

## <a name="example"></a>Przykład

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Zobacz też

- [Polecenie Oceń instrukcję](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
