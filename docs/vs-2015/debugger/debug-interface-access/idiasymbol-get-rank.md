---
title: 'IDiaSymbol:: get_rank | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf7c39213ae2eb233509d720b7e7c2eab0a17560
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64809711"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera rangę (liczbę wymiarów) Pascal wielowymiarowej tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca liczbę wymiarów w wielowymiarowej tablicy Pascal.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ranga odnosi się do liczby wymiarów w tablicy, w której jest zadeklarowana tablica `myarray[1,2,3]` . Ten przykład ma rangę 3 i 3 Wymiary. Ranga nie ma zastosowania do języka C++, który używa koncepcji tablicy tablic dla każdego wymiaru (to oznacza, `myarray[1][2][3]` ).  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
