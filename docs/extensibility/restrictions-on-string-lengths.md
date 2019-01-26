---
title: Ograniczenia długości ciągów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 679737b9590cd018f0de16298391351aedb0ac94
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929955"
---
# <a name="restrictions-on-string-lengths"></a>Ograniczenia długości ciągów
Interfejs API wtyczki kontroli źródła ogranicza długości ciągów używanych w różnych funkcji.  
  
## <a name="string-length-values"></a>Wartości długości ciągu  
  
|Stała|Wartość|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Długość nie obejmuje kończących się `null`. Inne stałych z sufiksem "_rozmiar" zamiast "_LEN" uwzględnić miejsce do zakończenia `null`.  
  
|Stała|Wartość|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Zobacz także  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)