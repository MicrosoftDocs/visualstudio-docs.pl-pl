---
title: EVALFLAGS90 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 943609ed841029017d77082cc44bde3abc083561
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723605"
---
# <a name="evalflags90"></a>EVALFLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wylicza prawidłowe wartości dla flagi sterujące Obliczanie wyrażenia. To wyliczenie rozszerza [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```csharp  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 EVAL90_RETURNVALUE  
 Określa, że wartość zwracana, jeśli istnieje, można obliczyć.  
  
 EVAL90_NOSIDEEFFECTS  
 Określa, że efekty uboczne niemożliwe.  
  
 EVAL90_ALLOWBPS  
 Określa zatrzymywanie punktów przerwania.  
  
 EVAL90_ALLOWERRORREPORT  
 Określa, że raportów o błędach do hosta mają być dozwolone. Używane głównie do obliczenia wyrażenia w skrypcie w programie Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Funkcje wymusza, aby zostały uznane za adresów, zamiast wywoływania funkcji.  
  
 EVAL90_NOFUNCEVAL  
 Funkcja zapobiega oceniane. Na przykład, rozważmy `int` tokenu w wyrażeniu `myExpression(int) + 10`. Ta funkcja może być poprawnie określona jako adres, ale nie jako wartość.  
  
 EVAL90_NOEVENTS  
 Flaga wskazująca, że zdarzenia, które wystąpiły podczas obliczania wyrażenia nie powinny być wysyłane, Menedżer debugowania sesji (SDM) lub środowiska IDE.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Umożliwia obliczanie wyrażenia czasu projektowania.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Umożliwia niejawne Tworzenie zmiennej.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Obliczanie wymusza natychmiastowe. Jest to przydatne podczas obsługi żądania, takie jak żądania użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

