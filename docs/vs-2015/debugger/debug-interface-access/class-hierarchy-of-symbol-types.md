---
title: Klasa Hierarchia typów symboli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c400479f761cb7d1bbe02c1aedade916da5596a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793038"
---
# <a name="class-hierarchy-of-symbol-types"></a>Hierarchia klas typów symboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W poniższej tabeli opisano typy symbol w hierarchii klas.  
  
## <a name="symbol-types"></a>Typów symboli  
  
|Typ symbolu|Opis|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Symbol, który będzie używany do reprezentowania każdej klasy, struktury i Unii.|  
|[Typ wyliczeniowy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Symbol dla typów wyliczeniowych.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Symbol dla typów wskaźnika.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Symbol typy tablic.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Symbol dla typów podstawowych|  
|[Typedef (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Symbol, który wprowadza nazw dla innych typów.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Symbol, który będzie używany dla każdej klasy bazowej typu zdefiniowanego przez użytkownika (UDT).|  
|[Przyjaciel (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbol klasy przyjazne i Friend — funkcje.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbol sygnatur funkcji unikatowy.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbol dla każdego parametru do funkcji.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Symbol rozmiar tabeli wirtualnej.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Symbol dla tabeli wirtualnej.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Symbol dla typu zdefiniowanego przez dostawcę.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Symbol dla typu zdefiniowanego w metadanych.|  
|[Wymiar](../../debugger/debug-interface-access/dimension.md)|Symbol wymiary tablicy.|  
  
> [!NOTE]
>  Każdy może mieć właściwości, które zawierają informacje o symboli, a także odwołania do innych symboli. Te właściwości są podane w tematach pojedynczy symbol.  
  
## <a name="see-also"></a>Zobacz też  
 [Cv_access_e — wyliczenie](../../debugger/debug-interface-access/cv-access-e.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)



