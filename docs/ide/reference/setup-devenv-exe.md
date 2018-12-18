---
title: Przełącznik instalacji Devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: eca577c0e4646821262c953cf48256937eed386c
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948379"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

/ Setup Przełącz powoduje, że Visual Studio, aby scalić metadanych zasobów, które opisują, menu, paski narzędzi i grup poleceń, ze wszystkich dostępnych pakietów VSPackage.

## <a name="syntax"></a>Składnia

```shell
devenv /setup
```

## <a name="remarks"></a>Uwagi

Ten przełącznik nie przyjmuje żadnych argumentów. `devenv /setup` Polecenia jest zazwyczaj podawana jako ostatni krok w procesie instalacji programu. Korzystanie z `/setup` przełącznika nie można uruchomić programu Visual Studio.

> [!NOTE]
> Należy uruchomić `devenv` jako administrator, aby można było używać `/setup` przełącznika.

## <a name="example"></a>Przykład

Ten przykład przedstawia ostatni krok w instalacji wersji programu Visual Studio, która obejmuje pakietów VSPackage.

```shell
devenv /setup
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)