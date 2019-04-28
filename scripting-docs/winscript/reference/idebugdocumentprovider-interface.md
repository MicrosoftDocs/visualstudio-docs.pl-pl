---
title: Interfejs IDebugDocumentProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5632134c86b5aa0e3cb769a68d2d4cfd944ff35c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008680"
---
# <a name="idebugdocumentprovider-interface"></a>Interfejs IDebugDocumentProvider
Zapewnia metodę dla wystąpienia dokumentu na żądanie.  
  
## <a name="remarks"></a>Uwagi  
 Oznacza to, pośrednie podczas tworzenia wystąpienia dokumentu:  
  
- Zezwala na dokument, aby załadować, gdy jest to konieczne.  
  
- Zezwala na obiekt dokumentu, które mają zostać zawarte w debugerze IDE.  
  
- Zezwala na wiele sposobów, aby uzyskać dostęp do tego samego obiektu dokumentu.  
  
  To efektywnie oddziela dokument od dostawcy i umożliwia dostawcy zawierają dodatkowe informacje o kontekście czasu wykonywania.  
  
  Oprócz metod odziedziczone `IDebugDocumentInfo`, `IDebugDocumentProvider` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Powoduje, że dokument można utworzyć wystąpienia, jeśli jeszcze nie istnieje.|