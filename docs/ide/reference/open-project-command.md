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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565815"
---
# <a name="open-project-command"></a>Otwórz projekt, polecenie

Otwiera istniejący projekt lub rozwiązanie.

## <a name="syntax"></a>Składnia

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumenty

`filename`

Wymagany. Pełna ścieżka i nazwa pliku projektu lub rozwiązania do otwarcia.

> [!NOTE]
> Składnia argumentu `filename` wymaga, aby ścieżki zawierające spacje używały cudzysłowów.

## <a name="remarks"></a>Uwagi

Automatyczne uzupełnianie próbuje zlokalizować prawidłową ścieżkę i nazwę pliku podczas pisania.

To polecenie nie jest dostępne podczas debugowania.

## <a name="example"></a>Przykład

Poniższy przykład otwiera test projektu języka Visual **Basic1:**

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Zobacz też

- [Polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenie](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
