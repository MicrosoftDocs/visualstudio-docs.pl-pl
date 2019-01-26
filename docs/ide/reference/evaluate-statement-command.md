---
title: Evaluate Statement — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89f8eacc11e591545e1a542c0e1eeda3c45b7df3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002395"
---
# <a name="evaluate-statement-command"></a>Evaluate Statement — Polecenie
Oblicza i wyświetla daną instrukcję.

## <a name="syntax"></a>Składnia

```cmd
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argumenty
 `text` Wymagane. Instrukcja do oceny.

## <a name="remarks"></a>Uwagi
 Okno służące do wprowadzania **EvaluateStatement** polecenie Określa, czy znak równości (=) jest interpretowany jako operator porównania lub operator przypisania.

 W **polecenia** okna, znak równości (=) jest interpretowany jako operator porównania. Na przykład, jeśli wartości zmiennych `a` i `b` są różne, a następnie polecenie

```cmd
>Debug.EvaluateStatement(a=b)
```

 Zwraca wartość `false`.

 W **bezpośrednie** okna, z drugiej strony, znak równości (=) jest interpretowany jako operator przypisania. Tak na przykład polecenie

```cmd
>Debug.EvaluateStatement(a=b)
```

 przypiszą do zmiennej `a` wartość zmiennej `b`.

## <a name="example"></a>Przykład

```cmd
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Zobacz też

- [Drukuj, polecenie](../../ide/reference/print-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)