---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e844438f5262b6a218a5feb355e78fc8a2cd1da
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005361"
---
# <a name="locationtype"></a>LocationType
Wskazuje rodzaj informacji o lokalizacji zawarte w symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Elementy  
 `LocIsNull`  
 Informacje o lokalizacji jest niedostępny.  
  
 `LocIsStatic`  
 Lokalizacja jest statyczne.  
  
 `LocIsTLS`  
 Lokalizacja znajduje się w pamięci lokalnej wątku.  
  
 `LocIsRegRel`  
 Lokalizacja jest powiązane z wątkiem rejestru.  
  
 `LocIsThisRel`  
 Lokalizacja jest `this`— względna.  
  
 `LocIsEnregistered`  
 Lokalizacja znajduje się w rejestrze.  
  
 `LocIsBitField`  
 Lokalizacja jest polem bitowym.  
  
 `LocIsSlot`  
 Lokalizacja jest miejsce Microsoft Intermediate Language (MSIL).  
  
 `LocIsIlRel`  
 Lokalizacja jest powiązane z wątkiem MSIL.  
  
 `LocInMetaData`  
 Lokalizacja znajduje się w metadanych.  
  
 `LocIsConstant`  
 Lokalizacja jest wartością stałą.  
  
 `LocTypeMax`  
 Liczba typów lokalizacji, w tym wyliczeniu.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości dostępne dla [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) interfejsu są zależne od lokalizacji symbolu w pliku obrazu. Aby uzyskać więcej informacji, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Wartości w tym wyliczeniu są zwracane przez wywołanie [idiasymbol::get_locationtype —](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)