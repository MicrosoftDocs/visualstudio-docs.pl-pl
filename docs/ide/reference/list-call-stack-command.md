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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a122b9fbc97816b114ba2ff6274756f9e2093eef
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919165"
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
Opcjonalny. Ustawia bieżącą ramkę stosu i nie wyświetla danych wyjściowych.

## <a name="switches"></a>Przełączniki
Każdy przełącznik może być wywoływany przy użyciu kompletnego formularza lub krótkiej formy.

/Count:`number` [lub]/c:`number`

Opcjonalny. Maksymalna liczba stosów wywołań do wyświetlenia. Wartość domyślna to Unlimited.

/ShowTypes:`yes` &#124; `no``yes`&#124;`no`

Opcjonalny. Określa, czy mają być wyświetlane typy parametrów. Wartość domyślna to `yes`.

/ShowNames:`yes` &#124; `no``yes`&#124;`no`

Opcjonalny. Określa, czy mają być wyświetlane nazwy parametrów. Wartość domyślna to `yes`.

/ShowValues:`yes` &#124; `no``yes`&#124;`no`

Opcjonalny. Określa, czy mają być wyświetlane wartości parametrów. Wartość domyślna to `yes`.

/ShowModule:`yes` &#124; `no``yes`&#124;`no`

Opcjonalny. Określa, czy ma być wyświetlana nazwa modułu. Wartość domyślna to `yes`.

/ShowLineOffset:`yes` &#124; [lub]/#:`no``yes`&#124;`no`

Opcjonalna. Określa, czy ma być wyświetlane przesunięcie wiersza. Wartość domyślna to `no`.

/ShowByteOffset:`yes`&#124;`no` [or] /B:`yes`&#124;`no`

Opcjonalny. Określa, czy ma być wyświetlane przesunięcie bajtów. Wartość domyślna to `no`.

/ShowLanguage:`yes` &#124; `no``yes`&#124;`no`

Opcjonalna. Określa, czy ma być wyświetlany język. Wartość domyślna to `no`.

/IncludeCallsAcrossThreads:`yes`&#124;`no` [or] /I:`yes`&#124;`no`

Opcjonalny. Określa, czy dołączać wywołania do lub z innych wątków. Wartość domyślna to `no`.

/ShowExternalCode:`yes`&#124;`no`

Opcjonalny. Określa, czy Tylko mój kod ma być wyświetlana dla stosu wywołań. Gdy Tylko mój kod jest wyłączona, zostanie wyświetlony cały kod niebędący użytkownikiem. Gdy tylko mój kod jest włączona, kod niebędący użytkownikiem jest wyświetlany `[external]` jako w danych wyjściowych stosu wywołań.

Nici`n`

Opcjonalny. Wyświetla stosu wywołań dla wątku `n`. Jeśli żaden wątek nie zostanie określony, program wyświetla stosu wywołań dla bieżącego wątku.

## <a name="remarks"></a>Uwagi
Zmiany wprowadzone do argumentów lub przełączników stosują się do przyszłych wywołań tego polecenia. Jeśli zostanie wyświetlona wartość Debug. ListCallStackby, zostanie wyświetlony cały stos wywołań. Jeśli określisz indeks, na przykład

```cmd
Debug.ListCallStack 2
```

następnie bieżąca Ramka stosu jest ustawiona na tę ramkę (w tym przypadku druga ramka).

Możesz również napisać to polecenie przy użyciu wstępnie zdefiniowanego aliasu KB. Na przykład możesz wprowadzić

```cmd
kb 2
```

Aby ustawić bieżącą ramkę stosu na drugą klatkę.

## <a name="example"></a>Przykład

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Zobacz też

- [Lista dezasemblacji, polecenie](../../ide/reference/list-disassembly-command.md)
- [Lista wątków, polecenie](../../ide/reference/list-threads-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)