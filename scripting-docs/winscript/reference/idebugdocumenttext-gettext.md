---
title: 'IDebugDocumentText:: gettext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572083"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Pobiera znaki i/lub atrybuty znaków skojarzone z zakresem pozycji znaku.  
  
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
 podczas Lokalizacja początkowa zakresu pozycji znaku.  
  
 `pcharText`  
 [in. out] Bufor tekstowy znaku. Bufor musi być wystarczająco duży, aby można było przechowywać `cMaxChars` znaków. Jeśli ten parametr ma wartość NULL, metoda nie zwraca znaków.  
  
 `pstaTextAttr`  
 [in. out] Bufor atrybutu znaku. Bufor musi być wystarczająco duży, aby można było przechowywać `cMaxChars` znaków. Jeśli ten parametr ma wartość NULL, metoda nie zwraca atrybutów.  
  
 `pcNumChars`  
 [in. out] Liczba zwróconych znaków/atrybutów. Ten parametr musi być ustawiony na wartość zero przed wywołaniem tej metody.  
  
 `cMaxChars`  
 podczas Liczba znaków w zakresie pozycji znaku. Określa również maksymalną liczbę znaków do zwrócenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera znaki i/lub atrybuty znaków skojarzone z zakresem pozycji znaku. Zakres pozycji znaku jest określany na podstawie pozycji znaku i liczby znaków.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentText   interfejsu](../../winscript/reference/idebugdocumenttext-interface.md)  
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)