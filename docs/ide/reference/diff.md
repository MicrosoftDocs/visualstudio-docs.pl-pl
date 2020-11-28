---
title: -Diff (devenv.exe)
description: Dowiedz się, jak porównać dwa pliki przy użyciu przełącznika wiersza polecenia diff devenv.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a2ae3da5036134260f48dce8838571312d87bf2
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305499"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Porównuje dwa pliki. Różnice są wyświetlane w specjalnym oknie programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argumenty

- *SourceFile*

  Wymagane. Pełna ścieżka i nazwa pierwszego pliku, który ma zostać porównany.

- *TargetFile*

  Wymagane. Pełna ścieżka i Nazwa drugiego pliku, który ma zostać porównany.

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

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
