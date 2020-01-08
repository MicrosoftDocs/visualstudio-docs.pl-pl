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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567843"
---
# <a name="print-command"></a>Print — Polecenie

Oblicza wyrażenie lub Wyświetla określony tekst.

## <a name="syntax"></a>Składnia

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumenty

`text`

Wymagany. Wyrażenie, które ma zostać obliczone lub tekst do wyświetlenia.

## <a name="remarks"></a>Uwagi

Możesz użyć znaku zapytania (?) jako aliasu dla tego polecenia. Tak więc, na przykład, polecenie

```cmd
>Debug.Print expA
```

można również napisać jako

```cmd
? expA
```

Obie wersje tego polecenia zwracają bieżącą wartość wyrażenia `expA`.

## <a name="example"></a>Przykład

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Zobacz także

- [Oceń instrukcję, polecenie](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
