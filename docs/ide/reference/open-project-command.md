---
title: Otwórz projekt — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c1034fbbafa04af2d62526fdbb48812d64e050
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565815"
---
# <a name="open-project-command"></a>Otwórz projekt — polecenie

Otwiera istniejący projekt lub rozwiązanie.

## <a name="syntax"></a>Składnia

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumenty

`filename`

Wymagany. Pełna ścieżka i nazwa pliku projektu lub rozwiązania do otwarcia.

> [!NOTE]
> Składnia `filename` argumentu wymaga, aby ścieżki zawierające spacje używały znaków cudzysłowu.

## <a name="remarks"></a>Uwagi

Funkcja automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.

To polecenie jest niedostępne podczas debugowania.

## <a name="example"></a>Przykład

W poniższym przykładzie zostanie otwarty Visual Basic projektu **Test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
