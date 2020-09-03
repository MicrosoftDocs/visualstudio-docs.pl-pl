---
title: IntelliSenseHostFlags | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12945998b215e9082591fad514bd9c16ab789405
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203892"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa flagi hosta IntelliSense.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Elementy członkowskie|Opis|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Bufor kontekstu jest tylko do odczytu.|  
|`IHF_NOSEPARATESUBJECT`|Brak tekstu podmiotu. Bufor kontekstu zawiera funkcję IntelliSense-Target (oznacza `!IHF_READONLYCONTEXT` ).|  
|`IHF_SINGLELINESUBJECT`|Tekst tematu nie jest obsługiwany przez wiele wierszy.|  
|`IHF_FORCECOMMITTOCONTEXT`|Analogicznie jak `CanCommitIntoReadOnlyBuffer` .|  
|`IHF_OVERTYPE`|Edytowanie (w temacie lub kontekście) powinno odbywać się w trybie zastępowania.|  
  
## <a name="requirements"></a>Wymagania  
 SingleFileeditor. idl  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
