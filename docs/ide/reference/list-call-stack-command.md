---
title: Lista stosu wywołań — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f62852550c161566832a7ab78d4058d1d14028f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72748722"
---
# <a name="list-call-stack-command"></a>Lista stosu wywołań — Polecenie
Wyświetla bieżący stos wywołań.

## <a name="syntax"></a>Składnia

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Argumenty

`index`\
Element opcjonalny. Ustawia bieżącą ramkę stosu i nie wyświetla żadnych danych wyjściowych.

## <a name="switches"></a>Przełączniki
Każdy przełącznik można wywołać za pomocą jego pełnej formy lub krótkiego formularza.

/Count:`number` [lub] /C:`number`

Element opcjonalny. Maksymalna liczba stosów połączeń do wyświetlenia. Wartość domyślna jest nieograniczona.

/ShowTypes:`yes`&#124;`no` [lub] /T:`yes`&#124;`no`

Element opcjonalny. Określa, czy mają być wyświetlane typy parametrów. Wartością `yes`domyślną jest .

/ShowNames:`yes`&#124;`no` [lub] /N:`yes`&#124;`no`

Element opcjonalny. Określa, czy mają być wyświetlane nazwy parametrów. Wartością `yes`domyślną jest .

/ShowValues:`yes`&#124;`no` [lub] /V:`yes`&#124;`no`

Element opcjonalny. Określa, czy mają być wyświetlane wartości parametrów. Wartością `yes`domyślną jest .

/ShowModule:`yes`&#124;`no` [lub] /M:`yes`&#124;`no`

Element opcjonalny. Określa, czy ma być wyświetlana nazwa modułu. Wartością `yes`domyślną jest .

/ShowLineOffset:`yes`&#124;`no` [lub] /#:`yes`&#124;`no`

Element opcjonalny. Określa, czy ma być wyświetlane przesunięcie linii. Wartością `no`domyślną jest .

/ShowByteOffset:`yes`&#124;`no` [lub] /B:`yes`&#124;`no`

Element opcjonalny. Określa, czy ma być wyświetlane przesunięcie bajtu. Wartością `no`domyślną jest .

/ShowLanguage:`yes`&#124;`no` [lub] /L:`yes`&#124;`no`

Element opcjonalny. Określa, czy język ma być wyświetlany. Wartością `no`domyślną jest .

/IncludeCallsAcrossThreads:`yes`&#124;`no` [lub] /I:`yes`&#124;`no`

Element opcjonalny. Określa, czy wywołania mają być dołączane do innych wątków, czy z nich. Wartością `no`domyślną jest .

/ShowExternalCode:`yes`&#124;`no`

Element opcjonalny. Określa, czy ma być wyświetlany tylko mój kod dla callstack. Gdy just my code jest wyłączony, wyświetlany jest cały kod niebędący użytkownikiem. Gdy tylko mój kod jest włączony, kod `[external]` niebędący użytkownikiem jest wyświetlany tak jak w danych wyjściowych callstack.

Wątku:`n`

Element opcjonalny. Wyświetla przywiązek wywoławczy dla wątku `n`. Jeśli nie wątek jest określony, wyświetla callstack dla bieżącego wątku.

## <a name="remarks"></a>Uwagi
Zmiany wprowadzone w argumentach lub przełącznikach dotyczą przyszłych wywołań tego polecenia. Jeśli problem Debug.ListCallStackby się, cały stos wywołań wyświetla. Jeśli określisz indeks, na przykład,

```cmd
Debug.ListCallStack 2
```

następnie bieżąca ramka stosu jest ustawiona na tę klatkę (w tym przypadku drugą klatkę).

Można również napisać to polecenie przy użyciu jego wstępnie zdefiniowanego aliasu kb. Można na przykład wprowadzić

```cmd
kb 2
```

, aby ustawić bieżącą klatkę stosu na drugą klatkę.

## <a name="example"></a>Przykład

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Zobacz też

- [Lista dezasemblacji — Polecenie](../../ide/reference/list-disassembly-command.md)
- [Lista wątków — Polecenie](../../ide/reference/list-threads-command.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)