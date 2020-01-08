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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
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

Opcjonalny. Adres pamięci, z którego ma zostać rozpoczęte wyświetlanie pamięci.

## <a name="switches"></a>Przełączniki
/ANSI&#124;Unicode

Opcjonalny. Wyświetl pamięć jako znaki odpowiadające bajtom pamięci, ANSI lub Unicode.

/Count:`number`

Opcjonalny. Określa liczbę bajtów pamięci do wyświetlenia, zaczynając od `expression`.

/Format:`formattype`

Opcjonalny. Typ formatu do wyświetlania informacji o pamięci w oknie **pamięci** ; może być OneByte, TwoBytes, FourBytes, EightBytes, float (32-bitowy) lub Double (64-bitowy). Jeśli OneByte jest używany, `/Unicode` jest niedostępny.

/Hex&#124;Signed&#124;Unsigned

Opcjonalny. Określa format wyświetlania liczb: jako podpisane, niepodpisane lub szesnastkowe.

## <a name="remarks"></a>Uwagi
Zamiast zapisywać kompletne polecenie **Debug. ListMemory —** ze wszystkimi przełącznikami, można wywołać polecenie przy użyciu wstępnie zdefiniowanych aliasów z określonymi przełącznikami ustawionymi na określone wartości. Na przykład zamiast wprowadzania:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

Można napisać:

```cmd
>df /Count:30 /Unicode
```

Poniżej znajduje się lista dostępnych aliasów dla polecenia **Debug. ListMemory —** :

|Alias|Polecenia i przełączniki|
|-----------| - |
|**d**|Debug.listmemory —|
|**da**|Debug.listmemory — /Ansi|
|**db**|Debug.listmemory — /Format:OneByte|
|**DC**|Debug.listmemory — /Format:FourBytes /Ansi|
|**dd**|Debug.listmemory — /Format:FourBytes|
|**DF**|Debug. ListMemory —/format: float|
|**dq**|Debug.listmemory — /Format:EightBytes|
|**du**|Debug.listmemory — /Unicode|

## <a name="example"></a>Przykład

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Zobacz także

- [Lista stosu wywołań, polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista wątków, polecenie](../../ide/reference/list-threads-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
