---
title: Idiasymbol::findchildren — | Dokumentacja firmy Microsoft
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
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 684fc0f5474e85806066de352da7ddad8527a3d2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809236"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera elementy podrzędne symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `symtag`  
 [in] Określa tagi symboli elementów podrzędnych, które mają zostać pobrane, zgodnie z definicją w [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md). Ustaw `SymTagNull` dla wszystkich elementów podrzędnych do pobrania.  
  
 `name`  
 [in] Określa nazwę elementy podrzędne, które mają zostać pobrane. Ustaw `NULL` dla wszystkich elementów podrzędnych do pobrania.  
  
 `compareFlags`  
 [in] Określa opcje porównywania stosowany do pasujących nazwy. Wartości z kolekcji [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md) wyliczenia można samodzielnie lub w połączeniu.  
  
 `ppResult`  
 [out] Zwraca [idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md) pobrać obiekt, który zawiera listę symbolami podrzędnymi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` Jeśli co najmniej jeden element podrzędny symbol został znaleziony lub zwraca `S_FALSE` Jeśli żadne elementy podrzędne nie znaleziono; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Metoda ta jest identyczna z wywoływaniem [idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md) metody za pomocą tego symbolu jako pierwszy parametr.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions, wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)



