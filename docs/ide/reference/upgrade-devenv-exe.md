---
title: -Upgrade (devenv.exe)
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
ms.openlocfilehash: 5bb2b296d8728587c9aa3c22b7a670d89612eff1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596427"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Aktualizuje plik rozwiązania i wszystkie jego pliki projektu lub plik projektu określony do bieżących formatów programu Visual Studio dla tych plików.

## <a name="syntax"></a>Składnia

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *Plik rozwiązania*

  Wymagane, jeśli uaktualniasz całe rozwiązanie i jego projekty. Ścieżka i nazwa pliku rozwiązania. Można wprowadzić tylko nazwę pliku rozwiązania lub pełną ścieżkę i nazwę pliku rozwiązania. Jeśli folder lub plik o nazwie jeszcze nie istnieje, jest tworzony.

- *Plik projektu*

  Wymagane, jeśli uaktualniasz jeden projekt. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić tylko nazwę pliku projektu lub pełną ścieżkę i nazwę pliku projektu. Jeśli folder lub plik o nazwie jeszcze nie istnieje, jest tworzony.

- `/Out`*Plik wyjściowy*

  Element opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Kopie zapasowe są automatycznie tworzone i kopiowane do katalogu o nazwie Kopia zapasowa utworzona w bieżącym katalogu.

Przed uaktualnieniem należy wyewidencjonować rozwiązania lub projekty kontrolowane przez źródła.

Za `/Upgrade` pomocą przełącznika nie otwiera visual studio. Wyniki uaktualnienia można zobaczyć w raporcie uaktualnienia dla języka programowania rozwiązania lub projektu. Nie są zwracane żadne informacje o błędzie lub użyciu. Aby uzyskać więcej informacji na temat uaktualniania projektów w programie Visual Studio, zobacz [Port, Migrate i Upgrade Visual Studio Projects](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Przykład

W tym przykładzie uaktualnia plik rozwiązania o nazwie "MyProject.sln".

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
