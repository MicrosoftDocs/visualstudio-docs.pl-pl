---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f739061217f3265945bead95e40129b86a173f8b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992922"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Określa informacje, które można pobrać o obiekt w ramce stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 FIF_FUNCNAME  
 Inicjowanie bądź użyj `m_bstrFuncName` pola.  
  
 FIF_RETURNTYPE  
 Inicjowanie bądź użyj `m_bstrReturnType` pola.  
  
 FIF_ARGS  
 Inicjowanie bądź użyj `m_bstrArgs` pola.  
  
 FIF_LANGUAGE  
 Inicjowanie bądź użyj `m_bstrLanguage` pola.  
  
 FIF_MODULE  
 Inicjowanie bądź użyj `m_bstrModule` pola.  
  
 FIF_STACKRANGE  
 Inicjowanie bądź użyj `m_addrMin` i `m_addrMax` pola (zakres stosu).  
  
 FIF_FRAME  
 Inicjowanie bądź użyj `m_pFrame` pola.  
  
 FIF_DEBUGINFO  
 Inicjowanie bądź użyj `m_fHasDebugInfo` pola.  
  
 FIF_STALECODE  
 Inicjowanie bądź użyj `m_fStaleCode` pola.  
  
 FIF_ANNOTATEDFRAME  
 Inicjowanie bądź użyj `m_fAnnotatedFrame` pola.  
  
 FIF_DEBUG_MODULEP  
 Inicjowanie bądź użyj `m_pModule` pola.  
  
 FIF_FUNCNAME_FORMAT  
 Formatuje nazwy funkcji. Wynik jest zwracany w `m_bstrFunName` pola i żadne inne pola są wypełnione.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Dodaje typ zwracany `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_ARGS  
 Dodaje argumenty `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_LANGUAGE  
 Dodaje języka `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_MODULE  
 Dodaje nazwę modułu, aby `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_LINES  
 Dodaje liczbę wierszy do `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_OFFSET  
 Dodaje do `m_bstrFuncName` pola przesunięcie w bajtach od początku wiersza, jeśli `FIF_FUNCNAME_LINES` jest określony. Jeśli `FIF_FUNCNAME_LINES` nie zostanie określony, lub jeśli numery wierszy nie są dostępne, dodaje przesunięcie w bajtach od początku funkcji.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Dodaje typ każdego argumentu funkcji `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Dodaje nazwę każdego argumentu funkcji `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Dodaje wartość każdego argumentu funkcji, aby `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Dodaje typu, nazwy i wartości wszystkich argumentów `m_bstrFuncName` pola.  
  
 FIF_ARGS_TYPES  
 Typy argumentów są pobierane i sformatowany.  
  
 FIF_ARGS_NAMES  
 Nazwy argumentów są pobierane i sformatowany.  
  
 FIF_ARGS_VALUES  
 Wartości argumentów są pobierane i sformatowany.  
  
 FIF_ARGS_ALL  
 Pobierz i sformatować typu, nazwy i wartości wszystkich argumentów.  
  
 FIF_ARGS_NOFORMAT  
 Określa, że argumenty nie są sformatowane (na przykład nie dodawać otwierających i zamykających nawiasów wokół listy argumentów ani dodać separator między argumentami).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Określa, że obliczanie funkcji (właściwość) nie powinien być używany podczas pobierania wartości argumentu.  
  
 FIF_FILTER_NON_USER_CODE  
 Aparat debugowania jest filtrowanie ramki kodu niepochodzącego od użytkownika, dzięki czemu nie są uwzględniane.  
  
 FIF_ARGS_NO_TOSTRING  
 Nie zezwalaj na `ToString()` funkcji oceny lub formatowania, gdy zwracany jest argumentów funkcji.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Informacji o ramce powinny być uzyskane z hostowanej domeny aplikacji, a nie procesu hostingu.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są przekazywane do [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) i [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metod, aby określić, które pola mają być inicjowane w [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury lub struktury.  
  
 Te flagi są również używane w celu wskazania, które pola [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury są używane i ważne, gdy struktura jest zwracany. Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)