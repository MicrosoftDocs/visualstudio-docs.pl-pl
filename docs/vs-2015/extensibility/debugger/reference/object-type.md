---
title: OBJECT_TYPE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a80f6533ccdc2a31ad9eac94e6c389a0e2abf254
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797367"
---
# <a name="objecttype"></a>OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa typ obiektu z Ewaluator wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```csharp  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 OBJECT_TYPE_BOOLEAN  
 Wskazuje, że obiekt jest wartością logiczną.  
  
 OBJECT_TYPE_CHAR  
 Wskazuje, że obiekt jest znakiem.  
  
 OBJECT_TYPE_I1  
 Wskazuje, że obiekt jest liczba całkowita ze znakiem jednobajtowych.  
  
 OBJECT_TYPE_U1  
 Wskazuje, że obiekt jest liczba całkowita bez znaku jednobajtowych.  
  
 OBJECT_TYPE_I2  
 Wskazuje, że obiekt jest liczba całkowita ze znakiem dwóch bajtów.  
  
 OBJECT_TYPE_U2  
 Wskazuje, że obiekt jest liczba całkowita bez znaku dwubajtowego.  
  
 OBJECT_TYPE_I4  
 Wskazuje, że obiekt jest całkowita czwartego bajtu.  
  
 OBJECT_TYPE_U4  
 Wskazuje, że obiekt jest liczba całkowita bez znaku czwartego bajtu.  
  
 OBJECT_TYPE_I8  
 Wskazuje, że obiekt jest całkowita 8 bajtową.  
  
 OBJECT_TYPE_U8  
 Wskazuje, że obiekt jest liczbą całkowitą bez znaku ośmiu bajtów.  
  
 OBJECT_TYPE_R4  
 Wskazuje, że obiekt jest czterobajtową liczbą zmiennoprzecinkową.  
  
 OBJECT_TYPE_R8  
 Wskazuje, że obiekt jest 8 bajtowa liczba zmiennoprzecinkowa.  
  
 OBJECT_TYPE_OBJECT  
 Wskazuje, że obiekt jest obiektem.  
  
 OBJECT_TYPE_NULL  
 Wskazuje, czy obiekt ma wartość NULL.  
  
 OBJECT_TYPE_CLASS  
 Wskazuje, że obiekt jest klasą.  
  
## <a name="remarks"></a>Uwagi  
 Przekazywany jako argument do [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) i [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

