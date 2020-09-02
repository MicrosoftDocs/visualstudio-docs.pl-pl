---
title: ButtonText — element | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184565"
---
# <a name="buttontext-element"></a>ButtonText, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To pole umożliwia określenie tekstu wyświetlanego w różnych menu. Domyślnie `ButtonText` element pojawia się na liście Kontrolery menu. `ButtonText`Element jest również domyślnym ustawieniem, jeśli inne pola tekstowe są puste. `ButtonText`Element nie może być pusty, nawet jeśli określono inne pola tekstowe.  
  
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
|[Strings, element](../extensibility/strings-element.md)|Grupuje elementy tekstowe, takie jak `ButtonText` i `CommandName` .|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa `ButtonText` elementu zawiera tekst wyświetlany dla elementów menu, kombi i innych elementów interfejsu użytkownika, które mają widoczny tekst.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
