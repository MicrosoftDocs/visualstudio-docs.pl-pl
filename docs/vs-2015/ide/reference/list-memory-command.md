---
title: List Memory — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672747"
---
# <a name="list-memory-command"></a>Lista pamięci — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla zawartość określonego zakresu pamięci.

## <a name="syntax"></a>Składnia

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argumenty
 `expression` opcjonalny. Adres pamięci, z którego ma zostać rozpoczęte wyświetlanie pamięci.

## <a name="switches"></a>Przełączniki
 /ANSI&#124;Unicode — opcjonalny. Wyświetl pamięć jako znaki odpowiadające bajtom pamięci, ANSI lub Unicode.

 /Count: `number` opcjonalny. Określa liczbę bajtów pamięci do wyświetlenia, zaczynając od `expression`.

 @No__t_0 opcjonalny. Typ formatu do wyświetlania informacji o pamięci w oknie **pamięci** ; może być OneByte, TwoBytes, FourBytes, EightBytes, float (32-bitowy) lub Double (64-bitowy). Jeśli OneByte jest używany, `/Unicode` jest niedostępny.

 /HEX&#124;podpisane&#124;nieoznaczone jako opcjonalne. Określa format wyświetlania liczb: jako podpisane, niepodpisane lub szesnastkowe.

## <a name="remarks"></a>Uwagi
 Zamiast zapisywać kompletne polecenie **Debug. ListMemory —** ze wszystkimi przełącznikami, można wywołać polecenie przy użyciu wstępnie zdefiniowanych aliasów z określonymi przełącznikami ustawionymi na określone wartości. Na przykład zamiast wprowadzania:

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 można napisać:

```
>df /Count:30 /Unicode
```

 Poniżej znajduje się lista dostępnych aliasów dla polecenia **Debug. ListMemory —** :

|Alias|Polecenia i przełączniki|
|-----------|--------------------------|
|**Wykres**|Debuguj. ListMemory —|
|**funkcją**|Debug. ListMemory —/ANSI|
|**bazą**|Debug. ListMemory —/format: OneByte|
|**DC**|Debug. ListMemory —/format: FourBytes/ANSI|
|**Dodaj**|Debug. ListMemory —/format: FourBytes|
|**DF**|Debug. ListMemory —/format: float|
|**elemencie DQ**|Debug. ListMemory —/format: EightBytes|
|**du**|Debug. ListMemory —/Unicode|

## <a name="example"></a>Przykład

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Zobacz też
 [Lista poleceń stosu wywołań](../../ide/reference/list-call-stack-command.md) [](../../ide/reference/list-threads-command.md) poleceń polecenie [Visual Studio](../../ide/reference/visual-studio-commands.md) Commands [okno](../../ide/reference/command-window.md) [Find/Command Box](../../ide/find-command-box.md) [Visual Studio Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
