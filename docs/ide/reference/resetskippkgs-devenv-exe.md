---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f797b6228124da8d8a998a6647dcfd9195ea92c
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948078"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Czyści wszystkie opcje, aby pominąć ładowanie dodane do VSPackages przez użytkowników, które chcą uniknąć obciążania problem pakietów VSPackage, a następnie uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Składnia

```cmd
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Uwagi
 Obecność tagu SkipLoading powoduje wyłączenie ładowania pakietu VSPackage; czyszczenie tagu włączające ładowania pakietu VSPackage.

## <a name="example"></a>Przykład
 Poniższy przykład czyści wszystkie tagi SkipLoading.

```cmd
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)