---
title: Dodaj istniejące polecenie projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 73d8e54938659920227b3614046b8a8f933023ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670211"
---
# <a name="add-existing-project-command"></a>Dodaj istniejący projekt — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dodaje istniejący projekt do bieżącego rozwiązania.

## <a name="syntax"></a>Składnia

```
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumenty
 `filename` opcjonalny. Pełna ścieżka i nazwa projektu, z rozszerzeniem, projektu do dodania do rozwiązania.

 Jeśli argument `filename` zawiera spacje, musi być ujęty w cudzysłów.

 Jeśli nazwa pliku nie zostanie określona, polecenie spowoduje otwarcie okna dialogowego plików, dzięki czemu użytkownik może wybrać projekt.

## <a name="remarks"></a>Uwagi
 Funkcja automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.

## <a name="example"></a>Przykład
 Ten przykład dodaje [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projekt, TestProject1 do bieżącego rozwiązania.

```
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
