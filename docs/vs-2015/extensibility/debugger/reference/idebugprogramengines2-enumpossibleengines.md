---
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182186"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zwraca identyfikatory GUID dla wszystkich możliwych aparatów debugowania (DE), które mogą debugować ten program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celtBuffer`  
 podczas Liczba wszystkich identyfikatorów GUID do zwrócenia. Określa również maksymalny rozmiar `rgguidEngines` tablicy.  
  
 `rgguidEngines`  
 [in. out] Tablica wszystkich identyfikatorów GUID do wypełnienia.  
  
 `pceltEngines`  
 określoną Zwraca rzeczywistą liczbę zwracanych identyfikatorów GUID.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` lub [C#] 0x8007007A, jeśli bufor nie jest wystarczająco duży.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić liczbę aparatów, należy wywołać tę metodę raz z `celtBuffer` parametrem ustawionym na 0, a `rgguidEngines` parametr ustawiony na wartość null. To zwraca `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A for C#), a `pceltEngines` parametr zwraca wymagany rozmiar buforu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
