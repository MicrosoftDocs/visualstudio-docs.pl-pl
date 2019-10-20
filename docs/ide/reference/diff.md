---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d438e9cea35cbf178658d8def78e264804240c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654512"
---
# <a name="diff-devenvexe"></a>/Diff (devenv. exe)

Porównuje dwa pliki. Różnice są wyświetlane w specjalnym oknie programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argumenty

- *SourceFile*

  Wymagany. Pełna ścieżka i nazwa pierwszego pliku, który ma zostać porównany.

- *TargetFile*

  Wymagany. Pełna ścieżka i Nazwa drugiego pliku, który ma zostać porównany.

- *SourceDisplayName*

  Opcjonalny. Nazwa wyświetlana pierwszego pliku.

- *TargetDisplayName*

  Opcjonalny. Nazwa wyświetlana drugiego pliku.

## <a name="remarks"></a>Uwagi

Jeśli wystąpienie IDE jest już otwarte, porównanie plików jest wyświetlane na karcie w bieżącym środowisku IDE.

## <a name="example"></a>Przykład

Pierwszy przykład porównuje dwa pliki bez zmiany ich nazw wyświetlanych. Drugi przykład porównuje pliki podczas zmiany obu nazw wyświetlanych. Trzeci i czwarty przykład porównują dwa pliki, ale stosuje alias tylko do pierwszego pliku lub drugiego pliku.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)
