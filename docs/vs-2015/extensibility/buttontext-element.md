---
title: ButtonText, Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35973241d1f68965680332fb3baf7c9b13c1bbcc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790217"
---
# <a name="buttontext-element"></a>ButtonText, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To pole pozwala określić tekst, który pojawia się w różnych menu. Domyślnie `ButtonText` element jest wyświetlany w menu kontrolerów. `ButtonText` Element staje się również wartość domyślna Jeśli inne pola tekstowe są puste. `ButtonText` Element nie może być pusta, nawet jeśli inne pola tekstowe są określone.  
  
## <a name="syntax"></a>Składnia  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Strings, element](../extensibility/strings-element.md)|Grupuje elementy tekstu, takie jak `ButtonText` i `CommandName`.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa elementu `ButtonText` element zawiera tekst, który jest wyświetlany dla elementów menu, combos i inne elementy interfejsu użytkownika, które mają widocznego tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

