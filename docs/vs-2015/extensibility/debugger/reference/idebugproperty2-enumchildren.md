---
title: 'IDebugProperty2:: EnumChildren | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cd5b29978b6b67cc80e95b86603b0caf487c26c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164954"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera listę elementów podrzędnych właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 podczas Kombinacja flag z wyliczenia [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , która określa, które pola w strukturze [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) wyliczane mają być wypełnione.  
  
 `dwRadix`  
 podczas Określa podstawy do użycia podczas formatowania dowolnych informacji numerycznych.  
  
 `guidFilter`  
 podczas Identyfikator GUID filtru używany z `dwAttribFilter` `pszNameFilter` parametrami i, aby wybrać elementy podrzędne, które mają `DEBUG_PROPERTY_INFO` zostać wyliczone. Na przykład `guidFilterLocals` filtry dla zmiennych lokalnych.  
  
 `dwAttribFilter`  
 podczas Kombinacja flag z wyliczenia [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , która określa typ obiektów do wyliczenia, na przykład `DBG_ATTRIB_METHOD` dla wszystkich metod, które mogą być elementami podrzędnymi tej właściwości. Używane w połączeniu z `guidFilter` `pszNameFilter` parametrami i.  
  
 `pszNameFilter`  
 podczas Nazwa filtru użyta z `guidFilter` parametrami i, `dwAttribFilter` Aby wybrać elementy podrzędne, które mają `DEBUG_PROPERTY_INFO` zostać wyliczone. Na przykład ustawienie tego parametru na filtry "MyX" dla wszystkich elementów podrzędnych o nazwie "MyX".  
  
 `dwTimeout`  
 podczas Określa maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Użyj `INFINITE` , aby czekać w nieskończoność.  
  
 `ppEnum`  
 określoną Zwraca obiekt [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) zawierający listę właściwości podrzędnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
