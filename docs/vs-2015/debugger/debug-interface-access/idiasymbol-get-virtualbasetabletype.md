---
title: Idiasymbol::get_virtualbasetabletype — | Dokumentacja firmy Microsoft
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
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e975cfdeff4d732c0b685665468705f6329702
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803594"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera typ wskaźnika wirtualnego tabeli podstawowej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`pRetVal`|[out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiektu, który określa typ tabeli podstawowej.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Wskaźnik wirtualnego tabeli podstawowej (`vbtptr`) jest ukryty wskaźnik w [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] wartości vtable, która obsługuje dziedziczenie z wirtualnej klasy bazowej. A `vbtptr` mogą mieć różne rozmiary, w zależności od klasy dziedziczone.  
  
 Ta metoda zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt, który może służyć do określenia rozmiaru vbtptr.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|DIA SDK w wersji 8.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



