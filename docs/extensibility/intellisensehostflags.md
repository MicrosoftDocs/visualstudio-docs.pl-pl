---
title: IntelliSenseHostFlags | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c7482e312dd767a62a18914f496e9b0835f7622b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833235"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Określa flagi hosta funkcji IntelliSense.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
### <a name="parameters"></a>Parametry  
  
|Elementy członkowskie|Opis|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Buforu kontekstu jest tylko do odczytu.|  
|`IHF_NOSEPARATESUBJECT`|Nie tekstu tematu. Bufor kontekst zawiera docelowy IntelliSense (implikuje `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Tekst tematu nie jest wielu-wiersza obsługą.|  
|`IHF_FORCECOMMITTOCONTEXT`|Taki sam jak `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Edytowanie (podmiotu lub w kontekście) ma się odbywać w trybie zastępowania.|  
  
## <a name="requirements"></a>Wymagania  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.TextManager.Interop>