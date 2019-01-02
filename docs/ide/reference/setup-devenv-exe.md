---
title: Przełącznik instalacji Devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3f1f801d4da451d9357082359a1cf001915e1041
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829277"
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