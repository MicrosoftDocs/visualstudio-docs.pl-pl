---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29cbcebc5bdc51be4223b2592bbe6ac3ae76525d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086362"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Umożliwia tworzenie obiektów w procesie aplikacji według kodu oznacza to poza procesem do aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateInstanceAtApplication(  
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
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplication, interfejs](../../winscript/reference/iremotedebugapplication-interface.md)