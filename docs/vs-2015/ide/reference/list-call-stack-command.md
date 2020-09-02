---
title: Lista poleceń stosu wywołań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c44ac18468fbd26adab2cf973a21df58ebb28c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657662"
---
# <a name="list-call-stack-command"></a>Lista stosu wywołań — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla bieżący stos wywołań.

## <a name="syntax"></a>Składnia

```
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Argumenty
 `index` Obowiązkowe. Ustawia bieżącą ramkę stosu i nie wyświetla danych wyjściowych.

## <a name="switches"></a>Przełączniki
 Każdy przełącznik może być wywoływany przy użyciu kompletnego formularza lub krótkiej formy.

 /Count: `number` [lub]/c: `number` opcjonalny. Maksymalna liczba stosów wywołań do wyświetlenia. Wartość domyślna to Unlimited.

 /ShowTypes: `yes`&#124;`no` [lub]/t: `yes`&#124;`no` opcjonalne. Określa, czy mają być wyświetlane typy parametrów. Wartość domyślna to `yes` .

 /ShowNames: `yes`&#124;`no` [lub]/n: `yes`&#124;`no` opcjonalne. Określa, czy mają być wyświetlane nazwy parametrów. Wartość domyślna to `yes` .

 /ShowValues: `yes`&#124;`no` [lub]/v: `yes`&#124;`no` opcjonalne. Określa, czy mają być wyświetlane wartości parametrów. Wartość domyślna to `yes` .

 /ShowModule: `yes`&#124;`no` [lub]/m: `yes`&#124;`no` opcjonalne. Określa, czy ma być wyświetlana nazwa modułu. Wartość domyślna to `yes` .

 /ShowLineOffset: `yes`&#124;`no` [lub]/#: `yes`&#124;`no` opcjonalne. Określa, czy ma być wyświetlane przesunięcie wiersza. Wartość domyślna to `no` .

 /ShowByteOffset: `yes`&#124;`no` [lub]/b: `yes`&#124;`no` opcjonalny. Określa, czy ma być wyświetlane przesunięcie bajtów. Wartość domyślna to `no` .

 /ShowLanguage: `yes`&#124;`no` [lub]/l: `yes`&#124;`no` opcjonalne. Określa, czy ma być wyświetlany język. Wartość domyślna to `no` .

 /IncludeCallsAcrossThreads: `yes`&#124;`no` [lub]/i: `yes`&#124;`no` opcjonalne. Określa, czy dołączać wywołania do lub z innych wątków. Wartość domyślna to `no` .

 /ShowExternalCode: `yes`&#124;`no` opcjonalny. Określa, czy Tylko mój kod ma być wyświetlana dla stosu wywołań. Gdy Tylko mój kod jest wyłączona, zostanie wyświetlony cały kod niebędący użytkownikiem. Gdy Tylko mój kod jest włączona, kod niebędący użytkownikiem jest wyświetlany jako `[external]` w danych wyjściowych stosu wywołań.

 Wątek: `n` opcjonalny. Wyświetla stosu wywołań dla wątku `n` . Jeśli żaden wątek nie zostanie określony, odstosu wywołań dla bieżącego wątku.

## <a name="remarks"></a>Uwagi
 Zmiany wprowadzone do argumentów lub przełączników stosują się do przyszłych wywołań tego polecenia. Jeśli zostanie wyświetlona wartość Debug. ListCallStackby, zostanie wyświetlony cały stos wywołań. Jeśli określisz indeks, na przykład

```
Debug.ListCallStack 2
```

 następnie bieżąca Ramka stosu jest ustawiona na tę ramkę (w tym przypadku druga ramka).

 Możesz również napisać to polecenie przy użyciu wstępnie zdefiniowanego aliasu KB. Na przykład możesz wprowadzić

```
kb 2
```

 Aby ustawić bieżącą ramkę stosu na drugą klatkę.

## <a name="example"></a>Przykład

```
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Zobacz też
 [Lista poleceń demontażu](../../ide/reference/list-disassembly-command.md) [listę wątków polecenie](../../ide/reference/list-threads-command.md) polecenia [Visual Studio](../../ide/reference/visual-studio-commands.md) Commands [okno](../../ide/reference/command-window.md) [Find/Command Box](../../ide/find-command-box.md) [Visual Studio Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
