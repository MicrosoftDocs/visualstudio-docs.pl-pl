---
title: -DoNotLoadProjects (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia DoNotLoadProjects devenv otworzyć określone rozwiązanie bez ładowania żadnych projektów.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb43d3a12e50d3f4a7af43721a5e93b769da28ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907585"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Nowość dla programu Visual Studio 2019 w wersji 16,1**

Otwiera określone rozwiązanie bez ładowania żadnych projektów. Aby uzyskać więcej informacji, zobacz [przefiltrowane rozwiązania w programie Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Składnia

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumenty

*SolutionName*

Wymagane. Pełna ścieżka i nazwa rozwiązania, które ma zostać otwarte.

## <a name="example"></a>Przykład

Przykład otwiera rozwiązanie MySln. sln bez ładowania żadnych projektów.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Zobacz też

- [Rozwiązania filtrowane w programie Visual Studio](../filtered-solutions.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
