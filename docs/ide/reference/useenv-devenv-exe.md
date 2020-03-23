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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596399"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Uruchamia program Visual Studio i ładuje niektóre zmienne środowiskowe do kompilacji.

> [!NOTE]
> Ten przełącznik jest zainstalowany z programem Desktop development z obciążeniem **języka C++.**

## <a name="syntax"></a>Składnia

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Pełna ścieżka i nazwa pliku rozwiązania.

- *Nazwaprojektu*

  Pełna ścieżka i nazwa pliku projektu.

## <a name="remarks"></a>Uwagi

Ten przełącznik wpływa na IDE programu Visual Studio we właściwościach projektu dla **katalogów VC++.** Jeśli `/UseEnv` zostanie określony przełącznik, węzeł **Katalogi VC++** wyświetla wartości zmiennych środowiskowych PATH, INCLUDE, LIBPATH i LIB. (Pokazuje również wartości **katalogów źródłowych** i **wykluczów katalogów**.) W przeciwnym razie węzeł zastępuje zmienne środowiskowe pięcioma wartościami katalogów: **Katalogi wykonywalne**, **Dołącz katalogi,** **Katalogi odwołań,** **Katalogi bibliotek**i **Katalogi Bibliotek WinRT**.

> [!TIP]
> Dostęp do właściwości projektu można uzyskać, klikając prawym przyciskiem myszy projekt C++ i wybierając polecenie **Właściwości**. W oknie dialogowym **Strony właściwości** wybierz pozycję **Właściwości konfiguracji,** a następnie pozycję **Katalogi VC++.**

Gdy nazwa projektu jest określona za pomocą tego przełącznika, narzędzie wyświetla zmienne środowiskowe dla wszystkich projektów w ramach rozwiązania nadrzędnego projektu.

## <a name="example"></a>Przykład

Poniższy przykład uruchamia Visual Studio i ładuje zmienne `MySolution` środowiskowe do stron właściwości rozwiązania.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Strona właściwości katalogów VC++ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
