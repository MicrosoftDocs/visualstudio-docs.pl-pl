---
title: -UseEnv (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a11d8eceec682e37f9bf34c79980c37880bdbe6
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948494"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Uruchamia programu Visual Studio i ładuje zmienne środowiskowe do **katalogi VC ++** okno dialogowe.

> [!NOTE]
> Ten przełącznik został zainstalowany przy użyciu **programowanie aplikacji klasycznych w języku C++** obciążenia.

## <a name="syntax"></a>Składnia

```shell
Devenv /useenv
```

## <a name="example"></a>Przykład

W poniższym przykładzie uruchamia programu Visual Studio i ładuje zmienne środowiskowe do **katalogi VC ++** okno dialogowe.

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>Zobacz także

* [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)