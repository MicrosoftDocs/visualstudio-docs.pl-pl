---
title: IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs
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
ms.openlocfilehash: 965147083bdc11a3544561fdd96cd85221ccd443
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410149"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Zwraca moduł wyliczający kontekstów wyrażenie znane przez ten składnik.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppedec`  
 [out] Moduł wyliczający kontekstów wyrażenie znane przez ten składnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesów używa tej metody, aby znaleźć wszystkie konteksty wyrażenia globalnego skojarzone z danym wątku.  
  
> [!NOTE]
> Ta metoda jest wywoływana z wewnątrz wątku zainteresowania. Jest implementujący do identyfikowania bieżącego wątku i zwraca moduł wyliczający odpowiednie.  
  
## <a name="see-also"></a>Zobacz też  
 [IProvideExpressionContexts, interfejs](../../winscript/reference/iprovideexpressioncontexts-interface.md)