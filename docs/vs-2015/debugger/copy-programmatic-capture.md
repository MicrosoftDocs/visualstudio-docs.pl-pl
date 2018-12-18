---
title: Kopiowanie (przechwycenie programowe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca2d6afc3a5693896c17e49ccb07b5152d906d43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776151"
---
# <a name="copy-programmatic-capture"></a>Kopiowanie (przechwycenie programowe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kopiuje zawartość active grafiki (.vsglog) pliku do nowego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szNewVSGLog`  
 Nazwa pliku nowy plik dziennika grafiki.  
  
## <a name="remarks"></a>Uwagi  
 Aby skopiować informacje graficzne do nowego pliku, muszą już udało się przechwycić pewne informacje grafiki; w przeciwnym razie nic się nie dzieje.



