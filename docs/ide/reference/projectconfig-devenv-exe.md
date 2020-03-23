---
title: -ProjectConfig (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8bb4b2860d40828a96e25ec6e6c73d947dd60c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567661"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Określa konfigurację kompilacji projektu, która ma być stosowana podczas tworzenia, czyszczenia, przebudowywanie lub wdrażanie projektu o nazwie w argumie. `/Project`

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

  Element opcjonalny. Nazwa konfiguracji rozwiązania (na `Debug` przykład `Release`lub ) do zastosowania do rozwiązania o nazwie w *SolutionName*. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład). Jeśli ten argument jest nieokreślony lub`""`pusty ciąg ( ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project`*Nazwa proj*

  Element opcjonalny. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Można również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig`*Nazwa ProjConfigName*

  Element opcjonalny. Nazwa konfiguracji kompilacji projektu (na przykład `Debug` lub `Release`) `/Project` do zastosowania do nazwanego. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład).

- `/Out`*Plik wyjściowy*

  Element opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Przełącznik `/ProjectConfig` musi być używany `/Project` z przełącznikiem `/Build`jako`Clean` `/Deploy`część `/Rebuild` , / , lub polecenia.

Łącz ciągi, które zawierają spacje w cudzysłowach.

Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie `/Out` polecenia lub w dowolnym pliku dziennika określonym za pomocą przełącznika.

## <a name="example"></a>Przykład

Następujące polecenie tworzy projekt, `CSharpWinApp`przy `Debug` użyciu konfiguracji `MySolution`kompilacji projektu w ramach:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Odbuduj (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
