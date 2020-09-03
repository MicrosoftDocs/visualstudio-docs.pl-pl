---
title: Ustaw bieżący proces | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665465"
---
# <a name="set-current-process"></a>Ustaw bieżący proces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia określony proces jako aktywny proces w debugerze.

## <a name="syntax"></a>Składnia

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumenty
 `index` Wymagane. Indeks procesu.

## <a name="remarks"></a>Uwagi
 Podczas debugowania można dołączyć do wielu procesów, ale tylko jeden proces jest aktywny w programie w danym momencie. Możesz użyć polecenia, `SetCurrentProcess` Aby ustawić aktywny proces.

## <a name="example"></a>Przykład

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Zobacz też
 [Visual Studio](../../ide/reference/visual-studio-commands.md) [polecenia polecenia —](../../ide/reference/command-window.md) [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
