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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaeab2e65088b8f1bfce3a6a12f8cd66c3245b75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747923"
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
Każdy przełącznik można wywołać za pomocą jego pełnej formy lub krótkiego formularza.

/count: `number` [lub] /c: `number` [lub] `number` /length: [lub] /l:`number`

Element opcjonalny. Liczba instrukcji do wyświetlenia. Wartość domyślna to 8.

/endaddress: `expression` [lub] /e:`expression`

Element opcjonalny. Adres, pod którym należy zatrzymać demontaż.

/codebytes:`yes`&#124;`no` [lub]`yes` /bajtów:&#124;`no` [lub] /b:`yes`&#124;`no`

Element opcjonalny. Wskazuje, czy mają być wyświetlane bajty kodu. Wartością `no`domyślną jest .

/źródło:`yes`&#124;`no` [lub] /s:`yes`&#124;`no`

Element opcjonalny. Wskazuje, czy kod źródłowy ma być wyświetlany. Wartością `no`domyślną jest .

/symbolnames:`yes`&#124;`no` [lub] /names:`yes`&#124;`no` [lub] /n:`yes`&#124;`no`

Element opcjonalny. Wskazuje, czy mają być wyświetlane nazwy symboli. Wartością `yes`domyślną jest .

 [/numery bielizny:`yes`&#124;`no`]

Element opcjonalny. Umożliwia wyświetlanie numerów wierszy skojarzonych z kodem źródłowym. Przełącznik /source musi mieć `yes` wartość, aby użyć przełącznika /linenumbers.

## <a name="example"></a>Przykład

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Zobacz też

- [Lista stosu wywołań — Polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista wątków — Polecenie](../../ide/reference/list-threads-command.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)