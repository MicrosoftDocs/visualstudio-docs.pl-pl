---
title: Funkcja SccEndBatch | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 986056b1f5202c2fb94d27a8792ed3b0fe308944
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799926"
---
# <a name="sccendbatch-function"></a>SccEndBatch, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja kończy partię operacji kontroli źródła. Partie te nie mogą być zagnieżdżone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Wsadowe operacji, które pomyślnie zakończone.|  
|SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Partie kontroli źródła są używane do wykonania tych samych operacji kontroli źródła, między wieloma projektami lub wieloma kontekstów. Partie można wyeliminować nadmiarowy okien dialogowych z interfejsu użytkownika podczas operacji wsadowej. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) i `SccEndBatch` do wskazywania początek i koniec operacji służą jako para funkcji. Nie można zagnieżdżać ich.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
