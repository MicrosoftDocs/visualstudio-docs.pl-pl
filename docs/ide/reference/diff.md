---
title: -Diff (devenv.exe)
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
ms.openlocfilehash: 4bb74501c15e961d8da8e1e29dd0d9979c79a305
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570092"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Porównuje dwa pliki. Różnice są wyświetlane w specjalnym oknie programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argumenty

- *Plik źródłowy*

  Wymagany. Pełna ścieżka i nazwa pierwszego pliku, który ma zostać porównany.

- *Plik docelowy*

  Wymagany. Pełna ścieżka i nazwa drugiego pliku, który ma zostać porównany.

- *Nazwa źródłaWyświetlania*

  Element opcjonalny. Wyświetlana nazwa pierwszego pliku.

- *Nazwa obiektu docelowegoWyświetlać*

  Element opcjonalny. Wyświetlana nazwa drugiego pliku.

## <a name="remarks"></a>Uwagi

Jeśli wystąpienie IDE jest już otwarte, porównanie plików pojawia się na karcie w bieżącym IDE.

## <a name="example"></a>Przykład

W pierwszym przykładzie porównuje się dwa pliki bez zmiany ich nazw wyświetlanych. Drugi przykład porównuje pliki, zmieniając jednocześnie obie ich nazwy wyświetlane. W trzecim i czwartym przykładzie porównano dwa pliki, ale stosuje się alias tylko do pierwszego lub drugiego pliku.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
