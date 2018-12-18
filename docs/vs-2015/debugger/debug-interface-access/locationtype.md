---
title: Locationtype — | Dokumentacja firmy Microsoft
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
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a41eb64cc1a93f39a50187d54ecf556246f31913
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752852"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wskazuje rodzaj informacji o lokalizacji zawarte w symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol::get_locationtype —](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)



