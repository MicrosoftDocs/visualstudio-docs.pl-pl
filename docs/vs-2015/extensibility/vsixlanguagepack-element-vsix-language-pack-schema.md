---
title: VSIXLanguagePack — element (schemat pakietu Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd3ed1477d1c4d345e5fc6f6496d12044d4af244
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114235"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack — element (schemat pakietu językowego VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wymagany. Dostarcza element główny pakietu językowego VSIX. Pakiet językowy VSIX zawiera zlokalizowane informacje o instalacji pakietu VSIX.  
  
## <a name="syntax"></a>Składnia  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`xmlns`|Przestrzeń nazw XML, w której jest zdefiniowany schemat pakietu Language Pack VSIX.|  
  
## <a name="xmlns-attribute"></a>Atrybut xmlns  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Wymagany. Lokalizacja pliku, który definiuje schemat pakietów językowych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[LocalizedName, element](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Wymagany. Zlokalizowana nazwa rozszerzenia, które ma zostać zainstalowane.|  
|[LocalizedDescription, element](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Wymagany. Zlokalizowany opis rozszerzenia, które ma zostać zainstalowane.|  
|[MoreInfoURL, element](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Opcjonalny. Link do zlokalizowanych informacji o rozszerzeniu.|  
|[License, element](../extensibility/license-element-vsix-language-pack-schema.md)|Opcjonalny. Ścieżka zlokalizowanej wersji pliku licencji dla rozszerzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
## <a name="element-information"></a>Informacje o elementach  

:::row:::
    :::column:::
        Przestrzeń nazw
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Nazwa schematu
    :::column-end:::
    :::column:::
        Schemat pakietu Language Pack VSIX
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Plik walidacji
    :::column-end:::
    :::column:::
        VSIXLanguagePackSchema. xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Może być puste
    :::column-end:::
    :::column:::
        Nie
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pakietu językowego VSX](../extensibility/vsx-language-pack-schema-reference.md) [lokalizowania pakietów VSIX](../extensibility/localizing-vsix-packages.md) [schemat rozszerzenia VSIX schematu 1,0](/previous-versions/dd393700(v=vs.110))
