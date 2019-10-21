---
title: -UseEnv (devenv.exe)
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da7a5e1d3490ea8342e6a7b21e91552ae2e8fdf0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622407"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Uruchamia program Visual Studio i ładuje pewne zmienne środowiskowe do kompilacji.

> [!NOTE]
> Ten przełącznik jest instalowany z **programowaniem dla komputerów C++ stacjonarnych i** obciążeniem.

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

Ten przełącznik ma wpływ na środowisko IDE programu Visual Studio we właściwościach projektu dla **katalogów VC + +** . W przypadku określenia przełącznika `/UseEnv` w węźle **Katalogi VC + +** są wyświetlane wartości zmiennych środowiskowych Path, include, LIBPATH i lib. (Pokazuje również wartości **katalogów źródłowych** i **Wyklucz katalogi**). W przeciwnym razie w węźle są zastępowane zmienne środowiskowe o pięciu wartościach katalogu: **katalogi wykonywalne** **, katalogi,** **katalogi odwołań**, **katalogi bibliotek**i **katalogi WinRT**.

> [!TIP]
> Aby uzyskać dostęp do właściwości projektu, kliknij prawym przyciskiem myszy C++ projekt i wybierz polecenie **Właściwości**. W oknie dialogowym **strony właściwości** wybierz opcję **Właściwości konfiguracji** , a następnie **Katalogi VC + +** .

Jeśli dla tego przełącznika zostanie określona nazwa projektu, narzędzie wyświetli zmienne środowiskowe dla wszystkich projektów w rozwiązaniu nadrzędnym projektu.

## <a name="example"></a>Przykład

Poniższy przykład uruchamia program Visual Studio i ładuje zmienne środowiskowe do stron właściwości rozwiązania `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)
- [Strona właściwości katalogów VC + + (system Windows)](/cpp/build/reference/vcpp-directories-property-page)
