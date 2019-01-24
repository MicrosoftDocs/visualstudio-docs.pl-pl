---
title: IDebugSettingsCallback2::GetMetricDword | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricDword
ms.assetid: 831a5a1a-c4af-4520-9fdf-3a731aeff85c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af24655561bfd2855f545f42f71b47ed23970662
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752176"
---
# <a name="idebugsettingscallback2getmetricdword"></a>IDebugSettingsCallback2::GetMetricDword
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera wartość metryki nadać jej nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetMetricDword(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```csharp  
private int GetMetricDword(  
   string   pszType,  
   ref Guid guidSection,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszType`  
 [in] Typ metryki.  
  
 `guidSection`  
 [in] Unikatowy identyfikator sekcji.  
  
 `pszMetric`  
 [in] Nazwa metryki.  
  
 `pdwValue`  
 [out] Zwraca wartość metryki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
