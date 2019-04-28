---
title: Idiasymbol::get_virtualbasetabletype — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea59822ebc568e843433f28f6e9b23f4df96fdb2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387005"
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
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
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
