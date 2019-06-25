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
ms.openlocfilehash: 37326bbe44eed15a562f0d28c01eac02973a2487
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789261"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Powoduje uruchomienie programu Visual Studio i ładuje niektórych zmiennych środowiskowych dla kompilacji.

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

Ten przełącznik ma wpływ na program Visual Studio IDE we właściwościach projektu **katalogi VC ++**. Jeśli określisz `/UseEnv` przełączyć, **katalogi VC ++** węzeł zawiera wartości dla zmiennych środowiskowych PATH, INCLUDE, LIBPATH i LIB. (Wartości pokazuje także **katalogi źródłowe** i **Wyklucz katalogi**.) W przeciwnym razie węzeł zamienia zmienne środowiskowe wartości katalogowych pięciu: **Katalogi wykonywalne**, **katalogi plików nagłówkowych**, **odwoływać się do katalogów**, **katalogi bibliotek**, i **biblioteki WinRT Katalogi**.

> [!TIP]
> Dostęp do właściwości projektu, kliknij prawym przyciskiem myszy projekt języka C++ i wybierając **właściwości**. W **stron właściwości** okno dialogowe, wybierz opcję **właściwości konfiguracji** i następnie **katalogi VC ++**.

Kiedy nazwa projektu jest określona za pomocą tego przełącznika, narzędzie wyświetla zmienne środowiskowe dla wszystkich projektów w ramach rozwiązania nadrzędnego projektu.

## <a name="example"></a>Przykład

W poniższym przykładzie uruchamia programu Visual Studio i ładuje zmienne środowiskowe do stron właściwości `MySolution` rozwiązania.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [VC ++ Directories Property Page (Windows)](/cpp/ide/vcpp-directories-property-page)
