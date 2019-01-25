---
title: IDebugSettingsCallback2::GetMetricString | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricString
- GetMetricString
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f20348cdced520b4153f02d2320fcabcd266273d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774192"
---
# <a name="idebugsettingscallback2getmetricstring"></a>IDebugSettingsCallback2::GetMetricString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera ciąg wartość metryki nadać jej nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetMetricString(  
    LPCWSTR pszType,  
    REFGUID guidSection,  
    LPCWSTR pszMetric,  
    BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetMetricString(  
    string     pszType,  
    ref Guid   guidSection,  
    string     pszMetric,  
    out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszType`  
 [in] Typ metryki.  
  
 `guidSection`  
 [in] Unikatowy identyfikator sekcji.  
  
 `pszMetric`  
 [in] Nazwa metryki.  
  
 `pbstrValue`  
 [out] Zwraca ciąg wartość metryki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
