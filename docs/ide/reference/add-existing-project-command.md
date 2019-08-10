---
title: Dodaj istniejący projekt — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5a511e19394b397096a5a5ba2e339166454138e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926282"
---
# <a name="add-existing-project-command"></a>Dodaj istniejący projekt — Polecenie
Dodaje istniejący projekt do bieżącego rozwiązania.

## <a name="syntax"></a>Składnia

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumenty
`filename`\
Opcjonalny. Pełna ścieżka i nazwa projektu, z rozszerzeniem, projektu do dodania do rozwiązania.

`filename` Jeśli argument zawiera spacje, musi być ujęty w cudzysłów.

Jeśli nazwa pliku nie zostanie określona, polecenie spowoduje otwarcie okna dialogowego plików, dzięki czemu użytkownik może wybrać projekt.

## <a name="remarks"></a>Uwagi
Funkcja automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.

## <a name="example"></a>Przykład
Ten przykład dodaje [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekt, TestProject1 do bieżącego rozwiązania.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)