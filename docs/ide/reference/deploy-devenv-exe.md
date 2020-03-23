---
title: -Deploy (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8eeb1a03e584b0b39030ec56ca6945a2d5ced78
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570131"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Wdraża rozwiązanie po kompilacji lub przebudowy. Dotyczy tylko projektów kodu zarządzanego.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.

- *Nazwa SolnConfigName*

  Element opcjonalny. Nazwa konfiguracji rozwiązania (na `Debug` przykład `Release`lub ) do utworzenia rozwiązania o nazwie w *SolutionName*. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład). Jeśli ten argument jest nieokreślony lub`""`pusty ciąg ( ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project`*Nazwa proj*

  Element opcjonalny. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Można również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig`*Nazwa ProjConfigName*

  Element opcjonalny. Nazwy konfiguracji kompilacji projektu (na przykład `Debug` lub `Release`) `/Project` do użycia podczas tworzenia nazwanego. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład). Jeśli ten przełącznik jest określony, zastępuje *SolnConfigName* argument.

- `/Out`*Plik wyjściowy*

  Element opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Określony projekt musi być projektem wdrażania. Jeśli określony projekt nie jest projekt wdrożenia, gdy projekt, który został zbudowany jest przekazywana do wdrożenia, nie powiedzie się z błędem.

Łącz ciągi, które zawierają spacje w cudzysłowie podwójnym.

Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie **Polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika [/Out.](out-devenv-exe.md)

## <a name="example"></a>Przykład

W tym przykładzie `CSharpWinApp`wdraża `Release` projekt, przy `MySolution`użyciu konfiguracji kompilacji projektu w ramach .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Odbuduj (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
