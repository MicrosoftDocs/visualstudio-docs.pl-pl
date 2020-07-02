---
title: Lista dezasemblacji — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91319a8d25aaec6bdd676ed6d709dffc47100195
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770647"
---
# <a name="list-disassembly-command"></a>Lista dezasemblacji — Polecenie
Rozpoczyna proces debugowania i pozwala określić, jak błędy są obsługiwane.

## <a name="syntax"></a>Składnia

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Przełączniki
Każdy przełącznik może być wywoływany przy użyciu kompletnego formularza lub krótkiej formy.

/Count: `number` [lub]/c: `number` [lub]/length: `number` [lub]/l:`number`

Opcjonalny. Liczba instrukcji do wyświetlenia. Wartość domyślna to 8.

/endaddress: `expression` [lub]/e:`expression`

Opcjonalny. Adres, pod który ma zostać zatrzymany demontaż.

/codebytes: `yes`&#124;`no` [lub]/bytes: `yes`&#124;`no` [lub]/b: `yes`&#124;`no`

Opcjonalny. Wskazuje, czy mają być wyświetlane bajty kodu. Wartość domyślna to `no` .

/source: `yes`&#124;`no` [lub]/s: `yes`&#124;`no`

Opcjonalny. Wskazuje, czy ma być wyświetlany kod źródłowy. Wartość domyślna to `no` .

/symbolnames: `yes`&#124;`no` [lub]/names: `yes`&#124;`no` [lub]/n: `yes`&#124;`no`

Opcjonalny. Wskazuje, czy mają być wyświetlane nazwy symboli. Wartość domyślna to `yes` .

 [/linenumbers: `yes`&#124;`no` ]

Opcjonalny. Włącza wyświetlanie numerów wierszy skojarzonych z kodem źródłowym. Przełącznik/Source musi mieć wartość, `yes` Aby można było użyć przełącznika/linenumbers.

## <a name="example"></a>Przykład

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Zobacz także

- [Listing stosu wywołań — polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista wątków — polecenie](../../ide/reference/list-threads-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)