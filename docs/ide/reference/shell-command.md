---
title: Shell — Polecenie
description: Dowiedz się więcej na temat polecenia Shell i sposobu uruchamiania programów wykonywalnych z poziomu programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b520d3bedf31bc09dc0cf48e86777872176e2e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957624"
---
# <a name="shell-command"></a>Shell — Polecenie
Uruchamia programy wykonywalne z poziomu programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="syntax"></a>Składnia

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Argumenty
`path`

Wymagane. Ścieżka i nazwa pliku do wykonania lub dokumentu do otwarcia. Pełna ścieżka jest wymagana, jeśli określony plik nie znajduje się w jednym z katalogów w zmiennej środowiskowej PATH.

`args`

Opcjonalny. Wszystkie argumenty do przekazania do wywołanego programu.

## <a name="switches"></a>Przełączniki
/commandwindow [lub]/Command [lub]/c [lub]/cmd

Opcjonalny. Określa, że dane wyjściowe dla pliku wykonywalnego są wyświetlane w oknie **wiersza polecenia** .

/dir: `folder` [lub]/d: `folder`

Opcjonalny. Określa katalog roboczy, który ma zostać ustawiony podczas uruchamiania programu.

/outputWindow [lub]/Output [lub]/out [lub]//o

Opcjonalny. Określa, że dane wyjściowe dla pliku wykonywalnego są wyświetlane w oknie **danych wyjściowych** .

## <a name="remarks"></a>Uwagi
Przełączniki/dir/o/c należy określić bezpośrednio po `Tools.Shell` . Wszystkie elementy określone po nazwie pliku wykonywalnego są przekazane do niego jako argumenty wiersza polecenia.

Wstępnie zdefiniowanego aliasu `Shell` można użyć zamiast `Tools.Shell` .

> [!CAUTION]
> Jeśli `path` argument zawiera ścieżkę do katalogu, a także nazwę pliku, należy ująć całą nazwę ścieżki w cudzysłowie literału ("" "), tak jak w poniższym:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Każdy zestaw trzech podwójnych cudzysłowów ("" ") jest interpretowany przez `Shell` procesor jako pojedynczy znak podwójnego cudzysłowu. W ten sposób powyższy przykład faktycznie przekazuje następujący ciąg ścieżki do `Shell` polecenia:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Jeśli ciąg ścieżki nie zostanie ujęty w cudzysłowy literału ("" "), system Windows będzie używać tylko części ciągu do pierwszego odstępu. Na przykład jeśli powyższy ciąg ścieżki nie został prawidłowo ujęty w cudzysłów, system Windows szuka pliku o nazwie "program" znajdującego się w C:\ Katalog główny. Jeśli plik wykonywalny C:\Program.exe był rzeczywiście dostępny, nawet jeden instalowany przez nielegalne manipulowanie, system Windows podejmie próbę wykonania tego programu zamiast żądanego programu "c:\Program Files\SomeFile.exe".

## <a name="example"></a>Przykład
Następujące polecenie używa xcopy.exe, aby skopiować plik `MyText.txt` do `Text` folderu. Dane wyjściowe z xcopy.exe są wyświetlane zarówno w **oknie poleceń** , jak i w oknie **danych wyjściowych** .

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Okno Dane wyjściowe](../../ide/reference/output-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
