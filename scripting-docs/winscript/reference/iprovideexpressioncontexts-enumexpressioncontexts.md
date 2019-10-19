---
title: 'IProvideExpressionContexts:: EnumExpressionContexts | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f161c1591267af1398d5c04d00623381cfae2ad4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572389"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Zwraca moduł wyliczający kontekstów wyrażenia znanych przez ten składnik.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppedec`  
 określoną Moduł wyliczający kontekstów wyrażenia znany przez ten składnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesów używa tej metody do znajdowania wszystkich kontekstów wyrażenia globalnego skojarzonych z danym wątkiem.  
  
> [!NOTE]
> Ta metoda jest wywoływana z poziomu wątku zainteresowania. Aby zidentyfikować bieżący wątek i zwrócić odpowiedni moduł wyliczający, należy do realizatora.  
  
## <a name="see-also"></a>Zobacz także  
 [IProvideExpressionContexts, interfejs](../../winscript/reference/iprovideexpressioncontexts-interface.md)