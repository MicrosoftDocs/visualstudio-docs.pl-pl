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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567778"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identyfikuje pojedynczy projekt w ramach określonej konfiguracji rozwiązania do kompilowania, czyszczenia, odbudowy lub wdrożenia.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Wymagany. [Kompiluje](build-devenv-exe.md), [czyści](clean-devenv-exe.md), [wdraża](deploy-devenv-exe.md)lub ponownie [kompiluje](rebuild-devenv-exe.md) projekt.

- *SolnConfigName*

  Opcjonalny. Nazwa konfiguracji rozwiązania (taka jak `Debug` lub `Release`) zastosowana do rozwiązania o nazwie w *SolutionName*. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32`). Jeśli ten argument jest nieokreślony lub pusty ciąg (`""`), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Możesz również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig` *ProjConfigName*

  Opcjonalny. Nazwa konfiguracji kompilacji projektu (na przykład `Debug` lub `Release`), która ma zostać zastosowana do `/Project` o nazwie. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32`).

- `/Out` *OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

- Musi być użyta część `/Build``devenv`, `/Clean`, `/Rebuild`lub `/Deploy`.

- Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

- Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie **wiersza polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika `/Out`.

## <a name="example"></a>Przykład

Ten przykład kompiluje `CSharpWinApp`projektu przy użyciu konfiguracji kompilacji projektu `Debug` w `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv. exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
