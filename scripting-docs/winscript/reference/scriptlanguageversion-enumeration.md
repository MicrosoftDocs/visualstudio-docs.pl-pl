---
title: Wyliczenie SCRIPTLANGUAGEVERSION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 374025b7564c058ae89064b6a27384c9075a30f9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350105"
---
# <a name="scriptlanguageversion-enumeration"></a>Wyliczenie SCRIPTLANGUAGEVERSION
Określa możliwości skryptów wersji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Domyślna wersja. Wartość całkowita wynosi 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting wersji 5.7. Wartość liczby całkowitej to 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting wersję 5.8. Wartość całkowita to 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Maksymalna wersja. Wartość całkowita wynosi 255.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kody błędów, stałe i wyliczenia aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)