---
title: Otwórz plik — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50e29e3182a19c9f3a667d41725327110b415fd0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591518"
---
# <a name="open-file-command"></a>Otwórz plik, polecenie

Otwiera istniejący plik i umożliwia określenie edytora.

## <a name="syntax"></a>Składnia

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty

`filename`

Wymagany. Pełna lub częściowa ścieżka i nazwa pliku do otwarcia. Ścieżki zawierające spacje muszą być ujęte w cudzysłów.

## <a name="switches"></a>Przełączniki

/e:`editorname`

Element opcjonalny. Nazwa edytora, w którym zostanie otwarty plik. Jeśli argument jest określony, ale nie podano nazwy edytora, zostanie wyświetlone okno dialogowe **Otwórz za pomocą.**

Składnia argumentu /e:`editorname` używa nazw edytorów wyświetlanych w oknie dialogowym Otwórz za pomocą, ujętych w cudzysłów.

Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy`editorname` wprowadzić następujące dla /e: argument.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi

Po wprowadzeniu ścieżki automatyczne uzupełnianie próbuje zlokalizować prawidłową ścieżkę i nazwę pliku.

## <a name="example"></a>Przykład

W tym przykładzie otwiera plik stylu "Test1.css" w edytorze kodu źródłowego.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też

- [Polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Okno bezpośrednie](../../ide/reference/immediate-window.md)
- [Pole Znajdź/Polecenie](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
