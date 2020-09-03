---
title: Otwórz polecenie projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99596442f3aef9e4cb2d890438d29b96cdf4f083
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671919"
---
# <a name="open-project-command"></a>Otwórz projekt — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otwiera istniejący projekt.

## <a name="syntax"></a>Składnia

```
File.OpenProject filename
```

## <a name="arguments"></a>Argumenty
 `filename` Wymagane. Pełna ścieżka i nazwa pliku projektu do otwarcia.

 Składnia `filename` argumentu wymaga, aby ścieżki zawierające spacje używały znaków cudzysłowu.

## <a name="remarks"></a>Uwagi
 Funkcja automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.

 To polecenie jest niedostępne podczas debugowania.

## <a name="example"></a>Przykład
 W tym przykładzie zostanie otwarty [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projekt, test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
