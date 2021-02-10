---
title: -ProjectConfig (devenv.exe)
description: Dowiedz się, jak użyć przełącznika wiersza polecenia ProjectConfig devenv, aby określić konfigurację kompilacji projektu do zastosowania podczas kompilowania, czyszczenia, odbudowywania lub wdrażania projektu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ba1f6f0de7e7b716853ec58aa27a34fe11010da4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969597"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Określa konfigurację kompilacji projektu, która ma zostać zastosowana podczas kompilowania, czyszczenia, odbudowywania lub wdrażania projektu o nazwie w `/Project` argumencie.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Wymagane. [Kompiluje](build-devenv-exe.md), [czyści](clean-devenv-exe.md), [wdraża](deploy-devenv-exe.md)lub ponownie [kompiluje](rebuild-devenv-exe.md) projekt.

- *SolnConfigName*

  Opcjonalny. Nazwa konfiguracji rozwiązania ( `Debug` na przykład lub `Release` ), która ma zostać zastosowana do rozwiązania o nazwie w *SolutionName*. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32` ). Jeśli ten argument jest nieokreślony lub jest ciągiem pustym ( `""` ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Możesz również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig`*ProjConfigName*

  Opcjonalny. Nazwa konfiguracji kompilacji projektu (taka jak `Debug` lub), `Release` która ma zostać zastosowana do `/Project` nazwanego. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32` ).

- `/Out`*OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

`/ProjectConfig`Przełącznik musi być używany z `/Project` przełącznikiem jako częścią `/Build` polecenia,/ `Clean` , `/Deploy` lub `/Rebuild` .

Ujmij ciągi, które zawierają spacje w podwójnych cudzysłowach.

Informacje podsumowujące dla kompilacji, w tym błędy, można wyświetlić w oknie polecenia lub w dowolnym pliku dziennika określonym za pomocą `/Out` przełącznika.

## <a name="example"></a>Przykład

Następujące polecenie kompiluje projekt `CSharpWinApp` przy użyciu `Debug` konfiguracji kompilacji projektu w `MySolution` :

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
