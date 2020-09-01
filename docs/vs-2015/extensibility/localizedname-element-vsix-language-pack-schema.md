---
title: Zlokalizowany element (schemat pakietu Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58e491290122a9d525ff8129333ac0f52ac5f778
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284358"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Zlokalizowany element (schemat pakietu Language Pack VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wymagany. Zlokalizowana nazwa rozszerzenia, które ma zostać zainstalowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Brak||  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element pakietu językowego VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Wymagany. Dostarcza element główny pakietu językowego VSIX.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wymagany. Nazwa pakietu językowego w języku docelowym.  
  
## <a name="element-information"></a>Informacje o elementach  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Przestrzeń nazw    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Nazwa schematu   |                 Schemat pakietu Language Pack VSIX                 |
| Plik walidacji |                VSIXLanguagePackSchema. xsd                 |
|  Może być puste   |                      Nie dotyczy                       |
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja schematu pakietu języka VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)   
 [Dokumentacja schematu rozszerzenia VSIX 1,0](/previous-versions/dd393700(v=vs.110))
