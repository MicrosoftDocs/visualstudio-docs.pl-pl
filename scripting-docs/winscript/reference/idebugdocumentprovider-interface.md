---
title: Interfejs IDebugDocumentProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345217"
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