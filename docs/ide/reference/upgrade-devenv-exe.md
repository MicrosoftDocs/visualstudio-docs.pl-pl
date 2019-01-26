---
title: -Upgrade (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d6554a167bd4515b65482a00ed724bf47e53dc2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923561"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Uaktualnia plik rozwiązania i wszystkie jego pliki projektu lub pliku projektu, określony do bieżącego formatu Visual Studio dla tych plików.

## <a name="syntax"></a>Składnia

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *SolutionFile*

  Wymagane, jeśli aktualizujesz całe rozwiązanie i jego projekty. Ścieżka i nazwa pliku rozwiązania. Można wprowadzić tylko nazwę pliku rozwiązania, lub pełną ścieżkę i nazwę pliku rozwiązania. Jeśli folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzony.

- *ProjectFile*

  Wymagane w przypadku uaktualniania jednego projektu. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić tylko nazwę pliku projektu, lub pełną ścieżkę i nazwę pliku projektu. Jeśli folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzony.

- `/Out` *OutputFilename*

  Opcjonalna. Nazwa pliku, który chcesz wysłać narzędzia danych wyjściowych do. Jeśli plik już istnieje, narzędzie dołączyło dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Kopie zapasowe są automatycznie tworzone i kopiowane do katalogu o nazwie kopia zapasowa, który jest tworzony w bieżącym katalogu.

Rozwiązania kontrolowanego źródła lub projekty musza być sprawdzone zanim będą mogły być uaktualnione.

Za pomocą `/Upgrade` przełącznik nie zaczyna się programu Visual Studio. Wyniki procesu uaktualniania można zobaczyć w raporcie uaktualnienia dla rozwoju języka rozwiązania lub projektu. Brak błędów i zużyciu informacji jest zwracana. Aby uzyskać więcej informacji na temat uaktualniania projektów w programie Visual Studio, zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Przykład

W tym przykładzie uaktualnia plik rozwiązania o nazwie "MyProject.sln".

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)