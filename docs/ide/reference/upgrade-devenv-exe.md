---
title: -Upgrade (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia upgrade devenv zaktualizować plik rozwiązania oraz wszystkie jego pliki projektu lub określony plik projektu do bieżących formatów programu Visual Studio dla tych plików.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bb0565783efb27cf4194bb25982ee0f717be776
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040956"
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

- `/Out`*OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

Kopie zapasowe są tworzone automatycznie i kopiowane do katalogu o nazwie Backup, który został utworzony w bieżącym katalogu.

Rozwiązania i projekty z kontrolą źródła muszą zostać wyewidencjonowane przed uaktualnieniem.

Użycie `/Upgrade` przełącznika nie powoduje otwarcia programu Visual Studio. Wyniki uaktualnienia można zobaczyć w raporcie uaktualnienia dla języka deweloperskiego rozwiązania lub projektu. Nie zwrócono informacji o błędzie ani użyciu. Aby uzyskać więcej informacji na temat uaktualniania projektów w programie Visual Studio, zobacz [port, migrowanie i uaktualnianie projektów programu Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Przykład

Ten przykład uaktualnia plik rozwiązania o nazwie "Moje projekty. sln".

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
