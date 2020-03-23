---
title: -Project (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- Project Devenv switch (/Project)
- Devenv, /Project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4b57a5bd51ff20de8da87798aa398db04bc1c7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567778"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identyfikuje pojedynczy projekt w ramach określonej konfiguracji rozwiązania do tworzenia, czyszczenia, przebudowy lub wdrażania.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Wymagany. [Tworzy,](build-devenv-exe.md) [czyści,](clean-devenv-exe.md) [wdraża](deploy-devenv-exe.md)lub [odbudowuje](rebuild-devenv-exe.md) projekt.

- *Nazwa SolnConfigName*

  Element opcjonalny. Nazwa konfiguracji rozwiązania (na `Debug` przykład `Release`lub) zastosowana do rozwiązania o nazwie w *rozwiązaniu SolutionName*. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład). Jeśli ten argument jest nieokreślony lub`""`pusty ciąg ( ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project`*Nazwa proj*

  Element opcjonalny. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Można również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig`*Nazwa ProjConfigName*

  Element opcjonalny. Nazwa konfiguracji kompilacji projektu (na przykład `Debug` lub `Release`) `/Project` do zastosowania do nazwanego. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład).

- `/Out`*Plik wyjściowy*

  Element opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

- Musi być używana `devenv` `/Build`część `/Clean` `/Rebuild`, `/Deploy` , lub polecenia.

- Łącz ciągi, które zawierają spacje w cudzysłowie podwójnym.

- Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie `/Out` **polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika.

## <a name="example"></a>Przykład

W tym przykładzie `CSharpWinApp`tworzy `Debug` projekt, przy `MySolution`użyciu konfiguracji kompilacji projektu w ramach .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Odbuduj (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
