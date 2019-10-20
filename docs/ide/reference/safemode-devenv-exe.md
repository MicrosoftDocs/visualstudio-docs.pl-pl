---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abaeded184db78085a9629da0e763b2f76dbd328
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655515"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Uruchamia program Visual Studio w trybie awaryjnym, ładując tylko domyślne środowisko i usługi.

## <a name="syntax"></a>Składnia

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Uwagi

Ten przełącznik zapobiega ładowaniu wszystkich pakietów VSPackage innych firm podczas uruchamiania programu Visual Studio, co pozwala na stabilne wykonanie.

## <a name="example"></a>Przykład

W poniższym przykładzie program Visual Studio jest uruchamiany w trybie awaryjnym.

```shell
devenv /safemode
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)