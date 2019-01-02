---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: ed14c3ec0da75df37c5a006f4e25240ac6630d20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949657"
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