---
title: 'IPropertyProxyEESide:: GetManagedViewerCreationData | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5161894875ac683e5a6e49ae623bd6025531006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199532"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera informacje o przeglądarce dla tego typu właściwości, aby utworzyć wystąpienie tej przeglądarki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `assemName`  
 określoną Zwraca nazwę zestawu, który znajduje się w tym obiekcie.  
  
 `assemBytes`  
 określoną Zwraca obiekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) zawierający bajty zestawu tego obiektu (jest to wartość null, jeśli nie są dostępne żadne bajty).  
  
 `assemPdb`  
 określoną Zwraca `IEEDataStorage` obiekt zawierający informacje o magazynie symboli dla tego obiektu (jest to wartość null, jeśli nie jest dostępny żaden magazyn symboli).  
  
 `className`  
 określoną Zwraca nazwę klasy zawierającej ten obiekt.  
  
 `alr`  
 określoną Zwraca wartość z wyliczenia [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) wskazującego lokalizację zestawu.  
  
 `replacementOk`  
 określoną Zwraca różną od zera ( `TRUE` ), jeśli wartość tego obiektu może być zmieniona; zero ( `FALSE` ), jeśli obiekt jest tylko do odczytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana przez Wizualizatory typów w celu utworzenia wystąpienia zarządzanej przeglądarki.  
  
## <a name="see-also"></a>Zobacz też  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
