---
title: Otwórz projekt — Polecenie
description: Dowiedz się więcej na temat polecenia Otwórz projekt i sposobu otwierania istniejącego projektu lub rozwiązania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ce00713cbfe862c5788a0131c99ba4c5750bb600
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304143"
---
# <a name="open-project-command"></a>Otwórz projekt — polecenie

Otwiera istniejący projekt lub rozwiązanie.

## <a name="syntax"></a>Składnia

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumenty

`filename`

Wymagane. Pełna ścieżka i nazwa pliku projektu lub rozwiązania do otwarcia.

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
