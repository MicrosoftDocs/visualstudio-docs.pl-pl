---
title: ButtonText, Element | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef22471d20df5582fec96c8a685029a1d475a4a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759123"
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
