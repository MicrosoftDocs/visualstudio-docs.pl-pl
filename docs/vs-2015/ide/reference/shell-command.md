---
title: Polecenie powłoki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ad49aadf6be56fb330b883050e6a6ff893cf054a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663540"
---
# <a name="shell-command"></a>Shell — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uruchamia programy wykonywalne z poziomu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Składnia

```
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Argumenty
 Wymagane `path`. Ścieżka i nazwa pliku do wykonania lub dokumentu do otwarcia. Pełna ścieżka jest wymagana, jeśli określony plik nie znajduje się w jednym z katalogów w zmiennej środowiskowej PATH.

 `args` opcjonalny. Wszystkie argumenty do przekazania do wywołanego programu.

## <a name="switches"></a>Przełączniki
 /commandwindow [lub]/Command [lub]/c [lub]/cmd opcjonalne. Określa, że dane wyjściowe dla pliku wykonywalnego są wyświetlane w oknie **wiersza polecenia** .

 /dir: `folder` [lub]/d: `folder` opcjonalne. Określa katalog roboczy, który ma zostać ustawiony podczas uruchamiania programu.

 /outputWindow [lub]/Output [lub]/out [lub]//o opcjonalne. Określa, że dane wyjściowe dla pliku wykonywalnego są wyświetlane w oknie **danych wyjściowych** .

## <a name="remarks"></a>Uwagi
 Przełączniki/dir/o/c należy określić bezpośrednio po `Tools.Shell`. Wszystkie elementy określone po nazwie pliku wykonywalnego są przekazane do niego jako argumenty wiersza polecenia.

 Wstępnie zdefiniowanego aliasu `Shell` można użyć zamiast `Tools.Shell`.

> [!CAUTION]
> Jeśli argument `path` podaje ścieżkę katalogu oraz nazwę pliku, należy ująć wszystkie nazwy ścieżki w cudzysłowy literału ("" "), tak jak w następujących przypadkach:

```
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

 Każdy zestaw trzech podwójnych cudzysłowów ("" ") jest interpretowany przez procesor `Shell` jako pojedynczy znak podwójnego cudzysłowu. W ten sposób powyższy przykład faktycznie przekazuje następujący ciąg ścieżki do polecenia `Shell`:

```
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Jeśli ciąg ścieżki nie zostanie ujęty w cudzysłowy literału ("" "), system Windows będzie używać tylko części ciągu do pierwszego odstępu. Na przykład jeśli powyższy ciąg ścieżki nie został prawidłowo ujęty w cudzysłów, system Windows szuka pliku o nazwie "program" znajdującego się w C:\ Katalog główny. Jeśli plik wykonywalny C:\Program.exe był rzeczywiście dostępny, nawet jeden instalowany przez nielegalne manipulowanie, system Windows podejmie próbę wykonania tego programu zamiast żądanego programu "c:\Program Files\SomeFile.exe".

## <a name="example"></a>Przykład
 Następujące polecenie używa xcopy. exe do skopiowania pliku `MyText.txt` do folderu `Text`. Dane wyjściowe z xcopy. exe są wyświetlane zarówno w **oknie poleceń** , jak i w oknie **danych wyjściowych** .

```
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Zobacz też
 Okno poleceń [poleceń programu Visual studio](../../ide/reference/visual-studio-commands.md) [](../../ide/reference/command-window.md) [okno dane wyjściowe](../../ide/reference/output-window.md) [pola Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
