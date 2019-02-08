---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
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
ms.openlocfilehash: 14b2ac3a80a9e17e0c554f56ae8e31ac32450c5e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938686"
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