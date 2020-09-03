---
title: -Safemode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28480399238c1c915056d3929f8fd188cfff7eca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665507"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uruchamia się [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w trybie awaryjnym, ładując tylko domyślne środowisko i usługi.

## <a name="syntax"></a>Składnia

```
devenv /SafeMode
```

## <a name="remarks"></a>Uwagi
 Ten przełącznik zapobiega ładowaniu wszystkich innych firm pakietów VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , co zapewnia stabilne wykonanie.

## <a name="description"></a>Opis
 Poniższy przykład jest uruchamiany [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w trybie awaryjnym.

## <a name="code"></a>Kod

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Zobacz też
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
