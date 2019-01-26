---
title: Lista pamięci — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6dca4d55d58f6fe4c2238fe881440f1bdd9e6661
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007493"
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

 Opcjonalna. Adres pamięci, od którego należy rozpocząć wyświetlanie pamięci.

## <a name="switches"></a>Przełączniki
 /ANSI&#124;Unicode

 Opcjonalna. Wyświetl pamięć jako znaki odpowiadający bajtów pamięci, ANSI lub Unicode.

 / Liczba:`number`

 Opcjonalna. Określa liczbę bajtów pamięci, aby wyświetlić, zaczynając od `expression`.

 / Format:`formattype`

 Opcjonalna. Formatowanie typ do wyświetlania informacji o pamięci w **pamięci** okna; może być OneByte TwoBytes, FourBytes, EightBytes, Float (32-bitowa) lub dwukrotnie (64-bitowe). Jeśli OneByte `/Unicode` jest niedostępny.

 /Hex&#124;Signed&#124;Unsigned

 Opcjonalna. Określa format wyświetlania liczb: jak podpisem, bez znaku lub szesnastkową.

## <a name="remarks"></a>Uwagi
 Zamiast pisania się kompletna **Debug.listmemory —** polecenia wszystkich przełączników, można wywołać polecenia przy użyciu wstępnie zdefiniowanych aliasów z przełącznikami, niektórych ustawień do określonej wartości. Na przykład zamiast wprowadzania:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 można napisać:

```cmd
>df /Count:30 /Unicode
```

 W tym miejscu znajduje się lista dostępnych aliasów dla **Debug.listmemory —** polecenia:

|Alias|Polecenia i przełączniki|
|-----------| - |
|**d**|Debug.listmemory —|
|**da**|Debug.listmemory — /Ansi|
|**db**|Debug.listmemory — /Format:OneByte|
|**dc**|Debug.listmemory — /Format:FourBytes /Ansi|
|**dd**|Debug.listmemory — /Format:FourBytes|
|**df**|Debug.listmemory — /Format:Float|
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