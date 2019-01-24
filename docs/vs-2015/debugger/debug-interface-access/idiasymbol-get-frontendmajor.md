---
title: Idiasymbol::get_frontendmajor — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMajor method
ms.assetid: f8a067c5-3306-4fc5-bc20-8910a47ed504
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7cdbf8af0370d2727a5f1b8e8e4ce1d4f1111770
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760652"
---
# <a name="idiasymbolgetfrontendmajor"></a>IDiaSymbol::get_frontEndMajor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera numer wersji głównej frontonu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_frontEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca numer wersji głównej frontonu. Zobacz uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Kompilatora zwykle składa się z dwóch podstawowe elementy: fronton (analizatora), która obsługuje analizowania kodu źródłowego w formie pośredniego, i zapleczem (generator kodu) konwertująca pośrednich formularza do zestawu. Nie jest niczym niezwykłym frontonu do innej wersji niż zaplecza.  
  
 Frontonu lub zaplecza numer wersji składa się z trzech części: \<główna >.\< pomocnicza >. \<kompilacji >, gdzie \<główne > jest główny numer wersji, \<pomocnicza > jest numerem wersji pomocniczej i \<kompilacji > jest numerem kompilacji. Na przykład 13.10.3077.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
