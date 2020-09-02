---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aaed99b669946f4d2885009ff328ce4e2e62fcae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204747"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta struktura reprezentuje adres względem `this` wskaźnika ( `Me` w Visual Basic).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagUNMANAGED_THIS_RELATIVE {  
   DWORD dwOffset;  
   DWORD dwBitOffset;  
   DWORD dwBitLength;  
} UNMANAGED_ADDRESS_THIS_RELATIVE;  
```  
  
```csharp  
public struct UNMANAGED_THIS_RELATIVE {  
   public uint dwOffset;  
   public uint dwBitOffset;  
   public uint dwBitLength;  
}  
```  
  
## <a name="terms"></a>Terminologia  
 dwOffset  
 Przesunięcie bajtowe z pozycji podstawowej (na przykład początek klasy tablic wirtualnych).  
  
 dwBitOffset  
 Przesunięcie w bitach z pozycji podstawowej (zawsze 0, chyba że odwołuje się do pola bitowego).  
  
 dwBitLength  
 Liczba bitów reprezentująca adres (zawsze 0, chyba że odwołuje się do pola bitowego).  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią Unii w strukturze [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , gdy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawione na `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (wartość z wyliczenia [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
