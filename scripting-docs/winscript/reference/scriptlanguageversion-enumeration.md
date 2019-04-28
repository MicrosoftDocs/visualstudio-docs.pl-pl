---
title: Wyliczenie SCRIPTLANGUAGEVERSION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aab63989d1ae02f7c75fc9c20a14d59e8a05078
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840216"
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