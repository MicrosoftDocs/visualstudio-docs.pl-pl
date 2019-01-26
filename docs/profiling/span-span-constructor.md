---
title: Konstruktor span::span | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d188f67a646d327c683125b7e59f208bdc7de61
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023215"
---
# <a name="spanspan-constructor"></a>span::span — Konstruktor
Inicjuje nowe wystąpienie klasy `span` klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
span(  
   const marker_series& _Series,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Series`  
 Kontekst serii prawidłowe znacznika.  
  
 `_Format`  
 Ciąg formatu złożonego, który zawiera tekst zmieszać z zero lub więcej elementów formatu, które odnoszą się do obiektów na liście argumentów.  
  
 `_Importance`  
 Poziom ważności.  
  
 `_Category`  
 Kategoria.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *cvmarkersobj.h*  
  
 **Namespace:** CONCURRENCY::Diagnostic —
 
 ## <a name="see-also"></a>Zobacz także
 [span, klasa](../profiling/span-class.md)