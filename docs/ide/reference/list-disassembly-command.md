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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b175c6b7e0fcd145d58318d89707cfd907acb2c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913377"
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

 /codebytes:`yes` &#124; `no` [i] /bytes:`yes` &#124; `no` [i] / b:`yes`&#124;`no`

 Opcjonalna. Wskazuje, czy mają być wyświetlane bajty kodu. Wartość domyślna to `no`.

 / source:`yes` &#124; `no` [i] / s:`yes`&#124;`no`

 Opcjonalna. Wskazuje, czy ma być wyświetlany kod źródłowy. Wartość domyślna to `no`.

 /symbolnames:`yes` &#124; `no` [i] /names:`yes` &#124; `no` [i] / n:`yes`&#124;`no`

 Opcjonalna. Wskazuje, czy mają być wyświetlane nazwy symboli. Wartość domyślna to `yes`.

 [/ linenumbers:`yes`&#124;`no`]

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