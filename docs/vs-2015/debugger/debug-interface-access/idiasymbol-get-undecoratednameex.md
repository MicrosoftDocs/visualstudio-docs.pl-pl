---
title: Idiasymbol::get_undecoratednameex — | Dokumentacja firmy Microsoft
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
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1902c6300a35924e7fcd626d9b63f69bc5bbc2c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745408"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera część lub całość nieozdobioną nazwę w przypadku języka C++ dekorowane nazwy (połączenie).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `undecoratedOptions`  
 [in] Określa kombinacja flag tę kontrolkę, co jest zwracana. Zobacz sekcję Spostrzeżenia, aby określone wartości i co robią.  
  
 `pRetVal`  
 [out] Zwraca nazwy ozdobionej nieozdobioną nazwę zawartej w języku C++.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 `undecorateOptions` Może być kombinacją następujących flag.  
  
> [!NOTE]
>  Nazwy flagi nie są zdefiniowane w DIA SDK, więc trzeba dodać deklaracji w kodzie albo użyj wartości w wierszach.  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Włącza pełne undecoration.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Usuwa wiodące znaki podkreślenia z firmy Microsoft rozszerzone słów kluczowych.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Wyłącza rozszerzenia rozszerzone słowa kluczowe firmy Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Wyłącza rozszerzenia typ zwracany dla podstawowej deklaracji.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Wyłącza rozszerzenia modelu deklaracji.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Wyłącza rozszerzenia języka Specyfikator deklaracji.|  
|UNDNAME_RESERVED1|0x0020|ZASTRZEŻONE.|  
|UNDNAME_RESERVED2|0x0040|ZASTRZEŻONE.|  
|UNDNAME_NO_THISTYPE|0x0060|Powoduje wyłączenie wszystkich modyfikatorów na `this` typu.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Wyłącza rozszerzenia specyfikatory dostępu dla członków.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Wyłącza rozszerzenia "throw-podpisów" dla funkcji i wskaźników do funkcji.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Wyłącza rozszerzenia `static` lub `virtual` elementów członkowskich.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Wyłącza rozszerzenia Microsoft model dla zwraca UDT.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates nazwy dekorowane w 32-bitowych.|  
|UNDNAME_NAME_ONLY|0x1000|Pobiera nazwę podstawowej deklaracji; po prostu zwraca [zakresu::] nazwa.  Rozwija parametry szablonu.|  
|UNDNAME_TYPE_ONLY|0x2000|Dane wejściowe to po prostu typ kodowania; Redaguj abstrakcyjnym deklaratorze.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Parametry szablonu rzeczywistych są dostępne.|  
|UNDNAME_NO_ECSU|0x8000|Pomija wyliczenia/klas/struct/union.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Pomija sprawdzanie prawidłowego identyfikatora znaków.|  
|UNDNAME_NO_PTR64|0x20000|Nie obejmuje ptr64 w danych wyjściowych.|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



