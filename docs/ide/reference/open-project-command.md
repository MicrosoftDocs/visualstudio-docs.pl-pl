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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e9249088b188fde1b346772ab1230d33160fe59
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996820"
---
# <a name="open-project-command"></a>Otwórz projekt — polecenie

Otwiera istniejący projekt lub rozwiązanie.

## <a name="syntax"></a>Składnia

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumenty

`filename`

Wymagana. Pełna ścieżka i nazwa projektu lub rozwiązania, aby otworzyć.

> [!NOTE]
> Składnia `filename` argument wymaga, że ścieżki zawierające spacje, użyj znaków cudzysłowu.

## <a name="remarks"></a>Uwagi

Automatyczne uzupełnianie próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.

To polecenie nie jest dostępne podczas debugowania.

## <a name="example"></a>Przykład

W poniższym przykładzie otwierany w projekcie języka Visual Basic **Test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Zobacz także

- [Polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)