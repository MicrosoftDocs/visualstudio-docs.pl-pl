---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b794c80768990a3abac85d3ea3b93699f3b220dd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970438"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Uruchamia programu Visual Studio w trybie awaryjnym, ładowanie tylko środowisko domyślne i usługi.

## <a name="syntax"></a>Składnia

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Uwagi

Ten przełącznik zapobiega wszystkich innych pakietów VSPackage ładowania po uruchomieniu programu Visual Studio, dzięki czemu wykonanie stabilne.

## <a name="example"></a>Przykład

Poniższy przykład uruchamia programu Visual Studio w trybie awaryjnym.

```shell
devenv /safemode
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)