---
title: IDebugDocumentText::GetText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77cc255bcd04754cbfde4638b67a85f6fdc0a922
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091991"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Pobiera znaki i/lub atrybuty znaków skojarzonych z zakresem pozycji znaku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 [in] Lokalizacja z zakresu znaków pozycja początkowa.  
  
 `pcharText`  
 [out w] Bufor tekstowy znaków. Rozmiar buforu musi być wystarczająco duży, aby pomieścić `cMaxChars` znaków. Jeśli ten parametr ma wartość NULL, metoda nie zwraca znaki.  
  
 `pstaTextAttr`  
 [out w] Buforu atrybut znaków. Rozmiar buforu musi być wystarczająco duży, aby pomieścić `cMaxChars` znaków. Jeśli ten parametr ma wartość NULL, metoda nie zwraca atrybutów.  
  
 `pcNumChars`  
 [out w] Zwracana liczba znaków i atrybuty. Ten parametr musi być równa zero przed wywołaniem tej metody.  
  
 `cMaxChars`  
 [in] Liczba znaków w zakresie pozycji znaku. Określa również maksymalną liczbę zwracanych znaków.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera znaki i/lub atrybuty znaków skojarzonych z zakresem pozycji znaku. Zakres pozycja znaku jest określony przez pozycji znaku i określonej liczby znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)