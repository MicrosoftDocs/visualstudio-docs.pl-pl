---
title: IDebugFunctionObject2::CreateObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdba52a1b4d97e3c00046d2057a9cf079208f43f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023044"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Tworzy obiekt, który używa konstruktora, używając podanej wartości ustawień flagi wersji ewaluacyjnej oraz wartość limitu czasu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pConstructor`  
 [in] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiekt, który reprezentuje konstruktora obiektu, który ma zostać utworzony.  
  
 `dwArgs`  
 [in] Liczba parametrów w `pArg` tablicy. Reprezentuje liczbę parametrów przekazanych do konstruktora.  
  
 `pArgs`  
 [in] Tablica [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów, które reprezentują parametry przekazywane do konstruktora.  
  
 `dwEvalFlags`  
 [in] Kombinacja flag z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenie określające sposób oceny ma zostać wykonane.  
  
 `dwTimeout`  
 [in] Maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj **NIESKOŃCZONEJ** czekanie w nieskończoność.  
  
 `ppObject`  
 [out] Zwraca **IDebugObject** reprezentujący nowo utworzony obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby utworzyć obiekt, który reprezentuje wystąpienie klasy lub inne typ złożony, który wymaga konstruktora, który jest parametrem.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)