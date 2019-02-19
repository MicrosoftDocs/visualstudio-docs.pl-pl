---
title: Ustaw bieżący proces | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be451ee1a0b4361e44c8be96713872ca0ee3bd76
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54768851"
---
# <a name="set-current-process"></a>Ustaw bieżący proces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Ustawia określony proces jako aktywny procesu w debugerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Wymagana. Indeks procesu.  
  
## <a name="remarks"></a>Uwagi  
 Podczas debugowania, ale tylko jeden proces jest aktywny w programie do usuwania błędów w dowolnym momencie można dołączyć do wielu procesów. Możesz użyć `SetCurrentProcess` polecenie, aby ustawić aktywny proces.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
