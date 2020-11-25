---
title: -UseEnv (devenv.exe)
description: Dowiedz się, jak uruchomić program Visual Studio przy użyciu przełącznika wiersza polecenia UseEnv devenv i załadować pewne zmienne środowiskowe do kompilacji.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51b47156b73d81f427c08e62006dc6e457e5780b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040943"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Uruchamia program Visual Studio i ładuje pewne zmienne środowiskowe do kompilacji.

> [!NOTE]
> Ten przełącznik jest instalowany z **programowaniem aplikacji klasycznych w języku C++** .

## <a name="syntax"></a>Składnia

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Pełna ścieżka i nazwa pliku rozwiązania.

- *ProjectName*

  Pełna ścieżka i nazwa pliku projektu.

## <a name="remarks"></a>Uwagi

Ten przełącznik ma wpływ na środowisko IDE programu Visual Studio we właściwościach projektu dla **katalogów VC + +**. Jeśli określisz `/UseEnv` przełącznik, w węźle **Katalogi VC + +** są wyświetlane wartości zmiennych środowiskowych Path, include, LIBPATH i lib. (Pokazuje również wartości **katalogów źródłowych** i **Wyklucz katalogi**). W przeciwnym razie w węźle są zastępowane zmienne środowiskowe o pięciu wartościach katalogu: **katalogi wykonywalne** **, katalogi,** **katalogi odwołań**, **katalogi bibliotek** i **katalogi WinRT**.

> [!TIP]
> Aby uzyskać dostęp do właściwości projektu, kliknij prawym przyciskiem myszy projekt C++ i wybierz polecenie **Właściwości**. W oknie dialogowym **strony właściwości** wybierz opcję **Właściwości konfiguracji** , a następnie **Katalogi VC + +**.

Jeśli dla tego przełącznika zostanie określona nazwa projektu, narzędzie wyświetli zmienne środowiskowe dla wszystkich projektów w rozwiązaniu nadrzędnym projektu.

## <a name="example"></a>Przykład

Poniższy przykład uruchamia program Visual Studio i ładuje zmienne środowiskowe do stron właściwości `MySolution` rozwiązania.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Strona właściwości katalogów VC + + (system Windows)](/cpp/build/reference/vcpp-directories-property-page)
