---
title: -SafeMode (devenv.exe)
description: Dowiedz się, jak używać przełącznika wiersza polecenia devenv trybu awaryjnego, aby uruchomić program Visual Studio w trybie awaryjnym, ładując tylko domyślne środowisko i usługi.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d8f663ca581892ba3207acbb0271586c322bad2
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039879"
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

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
