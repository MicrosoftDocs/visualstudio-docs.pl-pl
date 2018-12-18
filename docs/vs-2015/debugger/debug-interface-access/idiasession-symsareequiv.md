---
title: Idiasession::symsareequiv — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb9b8833ca4e7d780677aca475ee13897dbb8fc8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780025"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sprawdza, czy dwa symbole są równoważne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `symbolA`  
 [in] Pierwszy [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt używany do porównania.  
  
 `symbolB`  
 [in] Drugi `IDiaSymbol` obiekt używany do porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Symbole są równoważne, funkcja zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`, symbole nie są równoważne. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



