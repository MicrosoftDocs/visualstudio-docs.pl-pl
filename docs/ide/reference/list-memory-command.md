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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb5e6181c2dbe9a79b2ab1d0859722de324d768e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610694"
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

/Count: `number`

Opcjonalny. Określa liczbę bajtów pamięci do wyświetlenia, zaczynając od `expression`.

/Format: `formattype`

Opcjonalny. Typ formatu do wyświetlania informacji o pamięci w oknie **pamięci** ; może być OneByte, TwoBytes, FourBytes, EightBytes, float (32-bitowy) lub Double (64-bitowy). Jeśli OneByte jest używany, `/Unicode` jest niedostępny.

/HEX&#124;podpisany&#124;bez znaku

Opcjonalny. Określa format wyświetlania liczb: jako podpisane, niepodpisane lub szesnastkowe.

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
|**Wykres**|Debuguj. ListMemory —|
|**funkcją**|Debug. ListMemory —/ANSI|
|**bazą**|Debug. ListMemory —/format: OneByte|
|**DC**|Debug. ListMemory —/format: FourBytes/ANSI|
|**Dodaj**|Debug. ListMemory —/format: FourBytes|
|**DF**|Debug. ListMemory —/format: float|
|**elemencie DQ**|Debug. ListMemory —/format: EightBytes|
|**du**|Debug. ListMemory —/Unicode|

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