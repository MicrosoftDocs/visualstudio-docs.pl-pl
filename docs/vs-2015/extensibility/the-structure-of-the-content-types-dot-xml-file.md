---
title: Struktura pliku Content_types]. XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9b1fd98b3812fbeca2597534a7177ba2f81ab138
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301235"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struktura pliku [Content_types].xml
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera informacje o rodzaju zawartości w pakiecie VSIX. Program Visual Studio używa pliku XML [Content_Types] do zainstalowania pakietu, ale nie instaluje samego pliku.  
  
> [!NOTE]
> Chociaż ten temat dotyczy tylko plików [Content_Type]. XML, które są używane w pakietach VSIX, typ pliku [Content_Types]. XML jest częścią standardu *Open Package Conventions (OPC)* . Aby uzyskać więcej informacji, zobacz [OPC: A New Standard for pakowanie danych](https://go.microsoft.com/fwlink/?LinkID=148207) w witrynie MSDN w sieci Web.  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano element główny oraz jego atrybuty i elementy podrzędne.  
  
### <a name="root-element"></a>Element główny  
  
|Element|Opis|  
|-------------|-----------------|  
|`Types`|Zawiera elementy podrzędne, które wyliczają typy plików w pakiecie VSIX.|  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Xmlns`|(Wymagane). Lokalizacja schematu używanego dla tego pliku [Content_Types]. XML.|  
  
### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Przypisane  
  
|                           Wartość                           |                Opis                |
|-----------------------------------------------------------|-------------------------------------------|
| http://schemas.openformats.org/package/2006/content-types | Lokalizacja schematu typów zawartości. |
  
### <a name="child-elements"></a>Elementy podrzędne  
 Element `Types` może zawierać dowolną liczbę `Default` elementów.  
  
|Element|Opis|  
|-------------|-----------------|  
|`Default`|Opisuje typ zawartości w pakiecie VSIX. Każdy typ pliku w pakiecie musi mieć własny `Default` elementu.|  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Extension`|Rozszerzenie nazwy pliku w pakiecie VSIX.|  
|`ContentType`|Opisuje rodzaj zawartości skojarzonej z rozszerzeniem nazwy pliku.|  
  
### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Przypisane  
 Program Visual Studio rozpoznaje następujące wartości `ContentType` dla skojarzonych typów `Extension`.  
  
|Wewnętrzny|ContentType|  
|---------------|-----------------|  
|zawierającego|tekst/zwykły|  
|pkgdef|tekst/zwykły|  
|xml|tekst/XML|  
|vsixmanifest|tekst/XML|  
|htm lub HTML|tekst/HTML|  
|RTF|Aplikacja/RTF|  
|formatach|Aplikacja/plik PDF|  
|GIF|obraz/GIF|  
|jpg lub JPEG|obraz/jpg|  
|TIFF|obraz/TIFF|  
|vsix|Aplikacja/zip|  
|kodu|Aplikacja/zip|  
|bibliotece|Aplikacja/oktet — strumień|  
|wszystkie inne typy plików|Aplikacja/oktet — strumień|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Następujący plik [Content_Types]. XML opisuje typowy pakiet VSIX.  
  
### <a name="code"></a>Kod  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Odwołanie do schematu rozszerzenia VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: nowy standard tworzenia pakietów danych](https://go.microsoft.com/fwlink/?LinkID=148207)
