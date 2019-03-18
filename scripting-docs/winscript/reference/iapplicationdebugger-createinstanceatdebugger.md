---
title: IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 601f20c530ec5e275139d1e70d3df58fa88cd715
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58147634"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Umożliwia tworzenie obiektów w procesie debugowania przez kod to znaczy poza procesem do debugera.  
  
> [!IMPORTANT]
>  Ta metoda nie powinny być implementowane, ponieważ zezwala ona na niezaufanego kodu do tworzenia obiektów dowolnego wątku zaufanych debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 [in] Klasa identyfikator (CLSID) obiektu do utworzenia.  
  
 `pUnkOuter`  
 [in] Jeśli `NULL`, obiekt nie został utworzony jako część agregacji. W przeciwnym razie `pUnkOuter` jest wskaźnikiem do obiektu agregacji `IUnknown` interfejsu (kontrolowanie `IUnknown`).  
  
 `dwClsContext`  
 [in] Kontekst do uruchamiania kodu wykonywalnego. Wartości te są pobierane z wyliczenia `CLSCTX`.  
  
 `riid`  
 [in] Identyfikator interfejsu używany do komunikacji z obiektem.  
  
 `ppvObject`  
 [out] Adres zmiennej wskaźnika, który otrzymuje wskaźnik interfejsu w `riid`. Po powrocie pomyślne *`ppvObject` znajduje się wskaźnik żądanego interfejsu. W przypadku awarii \* `ppvObject` zawiera `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda deleguje do `CoCreateInstance`.  
  
 Metoda nie jest obecnie zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [IApplicationDebugger, interfejs](../../winscript/reference/iapplicationdebugger-interface.md)