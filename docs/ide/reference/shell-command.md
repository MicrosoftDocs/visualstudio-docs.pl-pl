---
title: Shell — Polecenie
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf13c7624d6c9d8e64b79f653eb83a0c5f3b3f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565880"
---
# <a name="shell-command"></a>Shell — Polecenie
Uruchamia programy wykonywalne z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Składnia

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Argumenty
`path`

Wymagany. Ścieżka i nazwa pliku do wykonania lub dokumentu do otwarcia. Pełna ścieżka jest wymagana, jeśli określony plik nie znajduje się w jednym z katalogów w zmiennej środowiskowej PATH.

`args`

Element opcjonalny. Wszelkie argumenty, aby przekazać do wywoływanych programu.

## <a name="switches"></a>Przełączniki
/commandwindow [lub] /command [lub] /c [lub] /cmd

Element opcjonalny. Określa, że dane wyjściowe pliku wykonywalnego są wyświetlane w oknie **Polecenia.**

/dir:`folder` [lub] /d:`folder`

Element opcjonalny. Określa katalog roboczy, który ma być ustawiony po uruchomieniu programu.

/outputwindow [lub] /output [lub] /out [lub] /o

Element opcjonalny. Określa, że dane wyjściowe pliku wykonywalnego są wyświetlane w oknie **Dane wyjściowe.**

## <a name="remarks"></a>Uwagi
Przełączniki /dir /o/c muszą być `Tools.Shell`określone natychmiast po . Wszystko, co zostało określone po tym, jak nazwa pliku wykonywalnego jest przekazywana do niego jako argumenty wiersza polecenia.

Wstępnie zdefiniowany alias `Shell` może być używany `Tools.Shell`zamiast pliku .

> [!CAUTION]
> Jeśli `path` argument dostarcza ścieżkę katalogu, a także nazwę pliku, należy ująć całą nazwę ścieżki w cudzysłowy dosłowne (""),jak w następujący sposób:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Każdy zestaw trzech cudzysłowów ("""") jest interpretowany przez `Shell` procesor jako pojedynczy znak cudzysłowu. W związku z tym w poprzednim przykładzie `Shell` faktycznie przekazuje następujący ciąg ścieżki do polecenia:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Jeśli ciąg ścieżki nie zostanie ujęty w cudzysłowy (""), system Windows użyje tylko części ciągu do pierwszego spacji. Na przykład, jeśli ciąg ścieżki powyżej nie były cytowane poprawnie, system Windows będzie szukać pliku o nazwie "Program" znajduje się w C:\ katalogu głównego. Jeśli plik wykonywalny C:\Program.exe był rzeczywiście dostępny, nawet jeden zainstalowany przez nielegalne manipulowanie, system Windows próbowałby wykonać ten program zamiast żądanego programu "c:\Program Files\SomeFile.exe".

## <a name="example"></a>Przykład
Następujące polecenie używa xcopy.exe do `MyText.txt` skopiowania `Text` pliku do folderu. Dane wyjściowe z pliku xcopy.exe są wyświetlane zarówno w **oknie polecenia,** jak i w oknie **Wyjście.**

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Okno wyjściowe](../../ide/reference/output-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
