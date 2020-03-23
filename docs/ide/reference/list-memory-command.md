---
title: Lista pamięci — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c500b1b516c2b1ab1bc66b7970fccc4ec7a85baa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568714"
---
# <a name="list-memory-command"></a>Lista pamięci — Polecenie
Wyświetla zawartość określonego zakresu pamięci.

## <a name="syntax"></a>Składnia

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argumenty
`expression`

Element opcjonalny. Adres pamięci, od którego ma rozpocząć wyświetlanie pamięci.

## <a name="switches"></a>Przełączniki
/ANSI&#124;Unicode

Element opcjonalny. Wyświetla pamięć jako znaki odpowiadające bajtom pamięci, ansi lub unicode.

/Count:`number`

Element opcjonalny. Określa, ile bajtów pamięci ma `expression`być wyświetlanych, począwszy od .

/Format:`formattype`

Element opcjonalny. Typ formatu do wyświetlania informacji o pamięci w oknie **Pamięć;** może to być OneByte, TwoBytes, FourBytes, EightBytes, Float (32-bit) lub Double (64-bitowy). Jeśli onebyte jest `/Unicode` używany, jest niedostępny.

/Hex&#124;podpisana&#124;niepodpisane

Element opcjonalny. Określa format wyświetlania liczb: jako podpisany, niepodpisany lub szesnastkowy.

## <a name="remarks"></a>Uwagi
Zamiast wypisywać pełne polecenie **Debug.ListMemory** ze wszystkimi przełącznikami, można wywołać polecenie przy użyciu wstępnie zdefiniowanych aliasów z pewnymi przełącznikami ustawionymi wstępnie na określone wartości. Na przykład zamiast wprowadzania:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

można napisać:

```cmd
>df /Count:30 /Unicode
```

Oto lista dostępnych aliasów dla polecenia **Debug.ListMemory:**

|Alias|Polecenia i przełączniki|
|-----------| - |
|**D**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**Db**|Debug.ListMemory /Format:OneByte|
|**Dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**Dd**|Debug.ListMemory /Format:FourBytes|
|**Df**|Debug.ListMemory /Format:Float|
|**Dq**|Debug.ListMemory /Format:EightBytes|
|**Du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Przykład

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Zobacz też

- [Lista stosu wywołań — Polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista wątków — Polecenie](../../ide/reference/list-threads-command.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
