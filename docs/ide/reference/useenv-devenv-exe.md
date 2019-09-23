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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16443b30ccf6ba03a01df0234695d27e4cd909af
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186486"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Uruchamia program Visual Studio i ładuje pewne zmienne środowiskowe do kompilacji.

> [!NOTE]
> Ten przełącznik został zainstalowany przy użyciu **programowanie aplikacji klasycznych w języku C++** obciążenia.

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

Ten przełącznik ma wpływ na środowisko IDE programu Visual Studio we właściwościach projektu dla **katalogów VC + +** . Jeśli określisz `/UseEnv` przełącznik, w węźle **Katalogi VC + +** są wyświetlane wartości zmiennych środowiskowych Path, include, LIBPATH i lib. (Pokazuje również wartości **katalogów źródłowych** i **Wyklucz katalogi**). W przeciwnym razie węzeł zastępuje zmienne środowiskowe pięcioma wartościami katalogu: **Katalogi wykonywalne** **: katalogi**, **katalogi odwołań**, **katalogi bibliotek**i **katalogi WinRT biblioteki**.

> [!TIP]
> Aby uzyskać dostęp do właściwości projektu, kliknij prawym przyciskiem myszy C++ projekt i wybierz polecenie **Właściwości**. W oknie dialogowym **strony właściwości** wybierz opcję **Właściwości konfiguracji** , a następnie **Katalogi VC + +** .

Jeśli dla tego przełącznika zostanie określona nazwa projektu, narzędzie wyświetli zmienne środowiskowe dla wszystkich projektów w rozwiązaniu nadrzędnym projektu.

## <a name="example"></a>Przykład

Poniższy przykład uruchamia program Visual Studio i ładuje zmienne środowiskowe do stron `MySolution` właściwości rozwiązania.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)
- [Strona właściwości katalogów VC + + (system Windows)](/cpp/build/reference/vcpp-directories-property-page)
