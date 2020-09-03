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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591518"
---
# <a name="open-file-command"></a>Otwórz plik — polecenie

Otwiera istniejący plik i umożliwia określenie edytora.

## <a name="syntax"></a>Składnia

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty

`filename`

Wymagany. Pełna lub częściowa ścieżka i nazwa pliku do otwarcia. Ścieżki zawierające spacje muszą być ujęte w cudzysłów.

## <a name="switches"></a>Przełączniki

/e`editorname`

Opcjonalny. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

Składnia/e: `editorname` argument używa nazw edytorów, jak pojawiają się w oknie dialogowym Otwórz za pomocą, ujętym w cudzysłów.

Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące polecenie/e: `editorname` argument.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi

Podczas wprowadzania ścieżki funkcja automatycznego uzupełniania próbuje znaleźć poprawną ścieżkę i nazwę pliku.

## <a name="example"></a>Przykład

Ten przykład otwiera plik stylu "test1. css" w edytorze kodu źródłowego.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Okno bezpośrednie](../../ide/reference/immediate-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
