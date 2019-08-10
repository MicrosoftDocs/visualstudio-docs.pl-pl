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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6d0b694f9703c6260d95ad03e085fcdf774dc52
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919131"
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

Liczbą`number`

Opcjonalny. Określa liczbę bajtów pamięci do wyświetlenia, rozpoczynając `expression`od.

Formatowanie`formattype`

Opcjonalny. Typ formatu do wyświetlania informacji o pamięci w oknie **pamięci** ; może być OneByte, TwoBytes, FourBytes, EightBytes, float (32-bitowy) lub Double (64-bitowy). Jeśli jest używana OneByte, `/Unicode` jest niedostępna.

/Hex&#124;Signed&#124;Unsigned

Opcjonalna. Określa format wyświetlania liczb: jako podpisane, niepodpisane lub szesnastkowe.

## <a name="remarks"></a>Uwagi
Zamiast zapisywać kompletne polecenie **Debug. ListMemory —** ze wszystkimi przełącznikami, można wywołać polecenie przy użyciu wstępnie zdefiniowanych aliasów z określonymi przełącznikami ustawionymi na określone wartości. Na przykład zamiast wprowadzania:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

można napisać:

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
|**Dodaj**|Debug.listmemory — /Format:FourBytes|
|**DF**|Debug. ListMemory —/format: float|
|**dq**|Debug.listmemory — /Format:EightBytes|
|**du**|Debug.listmemory — /Unicode|

## <a name="example"></a>Przykład

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Zobacz też

- [Lista stosu wywołań, polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista wątków, polecenie](../../ide/reference/list-threads-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)