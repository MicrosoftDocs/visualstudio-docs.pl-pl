---
title: Print — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 1677e05668b8681976447ef9ee401624d82bdd9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939832"
---
# <a name="print-command"></a>Print — Polecenie
Oblicza wyrażenie lub wyświetla określony tekst.

## <a name="syntax"></a>Składnia

```cmd
Debug.Print text
```

## <a name="arguments"></a>Argumenty
 `text`

 Wymagana. Wyrażenie do oceny lub tekst do wyświetlenia.

## <a name="remarks"></a>Uwagi
 Dla tego polecenia, można użyć znaku zapytania (?) jako alias. Tak na przykład polecenie

```cmd
>Debug.Print expA
```

 można również zapisać

```cmd
>? expA
```

 Obie wersje to polecenie zwraca bieżącą wartość wyrażenia `expA`.

## <a name="example"></a>Przykład

```cmd
>Debug.Print varA
```

## <a name="see-also"></a>Zobacz też

- [Oceń instrukcję, polecenie](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)