---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e69435a319a9730af846a912cb3f90a12d4ac8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918472"
---
# <a name="diff-devenvexe"></a>/ Diff (devenv.exe)

Porównuje dwa pliki. Różnice są wyświetlane w specjalne okno programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argumenty

- *SourceFile*

  Wymagana. Pełna ścieżka i nazwa pierwszego pliku do porównania.

- *TargetFile*

  Wymagana. Pełna ścieżka i nazwa drugiego pliku do porównania.

- *SourceDisplayName*

  Opcjonalna. Wyświetlana nazwa pierwszego pliku.

- *TargetDisplayName*

  Opcjonalna. Wyświetlana nazwa drugiego pliku.

## <a name="remarks"></a>Uwagi

Jeśli wystąpienie IDE jest już otwarty, porównanie plików pojawi się na karcie w bieżącym środowisku IDE.

## <a name="example"></a>Przykład

Pierwszy przykład porównuje dwa pliki bez zmiany ich nazw wyświetlanych. Drugi przykład porównuje pliki przy zmianie zarówno ich nazw wyświetlanych. Przykłady trzecia i czwarta Porównaj dwa pliki, ale alias dotyczą tylko pierwszego pliku lub drugiego pliku.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
