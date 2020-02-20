---
title: License — element (schemat pakietu Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1299d97cbda78049732d3367a9231272397e2ec
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477073"
---
# <a name="license-element-vsix-language-pack-schema"></a>License — element (schemat pakietu Language Pack VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcjonalny. Ścieżka zlokalizowanej wersji pliku licencji dla rozszerzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|None||  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element pakietu językowego VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Wymagany. Dostarcza element główny pakietu językowego VSIX.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Ścieżka względna zlokalizowanego pliku licencji, który ma zostać wyświetlony.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli element `License` jest zdefiniowany, tekst wyznaczonych licencji zostanie wyświetlony podczas instalacji, a użytkownik musi zaakceptować licencję, aby kontynuować.  
  
## <a name="element-information"></a>Informacje o elementach  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Przestrzeń nazw    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Nazwa schematu   |                 Schemat pakietu Language Pack VSIX                 |
| Plik walidacji |                VSIXLanguagePackSchema.xsd                 |
|  Może być puste   |                      Nie dotyczy                       |
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja schematu pakietu językowego VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)   
 [Dokumentacja schematu rozszerzenia VSIX 1,0](/previous-versions/dd393700(v=vs.110))
