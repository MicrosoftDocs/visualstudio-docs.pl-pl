---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6df78ec4be1fc94951634b84a98e80dc1403a41b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948741"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym, ładowanie tylko środowisko domyślne i usługi.

## <a name="syntax"></a>Składnia

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Uwagi
 Ten przełącznik uniemożliwia załadowanie, kiedy wszystkich innych pakietów VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozpoczyna się, co pozwala na zapewnienie stabilne wykonywania.

## <a name="description"></a>Opis
 Poniższy przykład rozpoczyna się [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym.

## <a name="code"></a>Kod

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)