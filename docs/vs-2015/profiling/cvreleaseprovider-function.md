---
title: Funkcja CvReleaseProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c59e5516129d5712983a228f68e4e91301656c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738813"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dostawca znacznika wydań. Zwalnianie dostawcy znacznika nie wpłynie na utworzonej wcześniej znaczników serii tego dostawcy. Seria znacznika musi to być wersja osobno przez wywołanie cvreleasemarkerseries —. Nie można zwolnić dostawcy powoduje, że przeciek pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Kontekst dostawcy. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, gdy dostawca jest pomyślnie zwolnione lub kod błędu w przypadku zostały wszystkie błędy. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)



