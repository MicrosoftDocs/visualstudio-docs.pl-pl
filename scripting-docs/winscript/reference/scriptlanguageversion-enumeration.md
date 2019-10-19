---
title: SCRIPTLANGUAGEVERSION, Wyliczenie | Microsoft Docs
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
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574361"
---
# <a name="scriptlanguageversion-enumeration"></a>Wyliczenie SCRIPTLANGUAGEVERSION
Określa możliwe wersje skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczeniowe  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Wersja domyślna. Wartość całkowita jest równa 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Obsługa skryptów systemu Windows w wersji 5,7. Wartość całkowita to 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Obsługa skryptów systemu Windows w wersji 5,8. Wartość całkowita to 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Maksymalna wersja. Wartość całkowita to 255.|  
  
## <a name="see-also"></a>Zobacz także  
 [Kody błędów, stałe i wyliczenia aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)