---
title: -Upgrade (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9894056babdd8615e4ae052eb73e91e9b108acc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622418"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Aktualizuje plik rozwiązania oraz wszystkie jego pliki projektu lub określony plik projektu do bieżących formatów programu Visual Studio dla tych plików.

## <a name="syntax"></a>Składnia

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *SolutionFile*

  Wymagane, Jeśli uaktualniasz całe rozwiązanie i jego projekty. Ścieżka i nazwa pliku rozwiązania. Można wprowadzić tylko nazwę pliku rozwiązania lub pełną ścieżkę i nazwę pliku rozwiązania. Jeśli folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzony.

- *ProjectFile*

  Wymagane w przypadku uaktualniania pojedynczego projektu. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Można wprowadzić tylko nazwę pliku projektu lub pełną ścieżkę i nazwę pliku projektu. Jeśli folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzony.

- `/Out` *OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

Kopie zapasowe są tworzone automatycznie i kopiowane do katalogu o nazwie Backup, który został utworzony w bieżącym katalogu.

Rozwiązania i projekty z kontrolą źródła muszą zostać wyewidencjonowane przed uaktualnieniem.

Użycie przełącznika `/Upgrade` nie powoduje otwarcia programu Visual Studio. Wyniki uaktualnienia można zobaczyć w raporcie uaktualnienia dla języka deweloperskiego rozwiązania lub projektu. Nie zwrócono informacji o błędzie ani użyciu. Aby uzyskać więcej informacji na temat uaktualniania projektów w programie Visual Studio, zobacz [port, migrowanie i uaktualnianie projektów programu Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Przykład

Ten przykład uaktualnia plik rozwiązania o nazwie "Moje projekty. sln".

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)