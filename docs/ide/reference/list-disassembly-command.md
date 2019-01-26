---
title: Lista dezasemblacji — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab169dba1ab6692c0a6df8665e20d2695c7ac2c5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028843"
---
# <a name="list-disassembly-command"></a>Lista dezasemblacji — Polecenie
Rozpoczyna proces debugowania i pozwala określić sposób obsługi błędów.

## <a name="syntax"></a>Składnia

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Przełączniki
 Każdy przełącznik może być wywoływany przy użyciu jego wypełniony formularz lub krótka.

 / count: `number` [i] / c: `number` [i] /length: `number` [i] / l: wyświetlenie `number`

 Opcjonalna. Liczba instrukcji do wyświetlenia. Wartość domyślna to 8.

 /endaddress: `expression` [i] / e: `expression`

 Opcjonalna. Adres, w którym można zatrzymać dezasemblacji.

 /codebytes:`yes`&#124;`no` [or] /bytes:`yes`&#124;`no` [or] /b:`yes`&#124;`no`

 Opcjonalna. Wskazuje, czy mają być wyświetlane bajty kodu. Wartość domyślna to `no`.

 /source:`yes`&#124;`no` [or] /s:`yes`&#124;`no`

 Opcjonalna. Wskazuje, czy ma być wyświetlany kod źródłowy. Wartość domyślna to `no`.

 /symbolnames:`yes`&#124;`no` [or] /names:`yes`&#124;`no` [or] /n:`yes`&#124;`no`

 Opcjonalna. Wskazuje, czy mają być wyświetlane nazwy symboli. Wartość domyślna to `yes`.

 [/linenumbers:`yes`&#124;`no`]

 Opcjonalna. Umożliwia wyświetlanie numerów wierszy skojarzonych z kodem źródłowym. Przełącznik/Source musi mieć wartość `yes` na używanie przełącznika /linenumbers.

## <a name="example"></a>Przykład

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Zobacz też

- [Lista stosu wywołań, polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista wątków, polecenie](../../ide/reference/list-threads-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)