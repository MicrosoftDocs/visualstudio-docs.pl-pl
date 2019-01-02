---
title: Struktura pliku [Content_types] .xml | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd4ed2783ba3b56004037338452722f3ea0f8ddc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909898"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Struktura pliku [Content_types].xml
Zawiera informacje na temat rodzajów zawartości w pakiecie VSIX. Program Visual Studio używa pliku [Content_Types] .xml, aby zainstalować pakiet, ale nie jest instalowana w samym pliku.  
  
> [!NOTE]
>  Mimo że w tym temacie mają zastosowanie tylko do plików XML [Content_Type], które są używane w pakietów VSIX, typu pliku [Content_Types] .xml jest częścią *otwarte konwencje tworzenia pakietów (OPC)* standardowych. Aby uzyskać więcej informacji, zobacz [OPC: Nowy Standard dla pakowania własnych danych](http://go.microsoft.com/fwlink/?LinkID=148207) w witrynie MSDN w sieci Web.  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 Poniższe sekcje opisują element główny i jego atrybuty i elementy podrzędne.  
  
### <a name="root-element"></a>Element główny  
  
|Element|Opis|  
|-------------|-----------------|  
|`Types`|Zawiera elementy podrzędne, które wyliczanie typów plików w pakiecie VSIX.|  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Xmlns`|(Wymagane). Lokalizacja schematu, używany dla tego pliku XML [Content_Types].|  
  
### <a name="attribute-name-attribute"></a>{Atrybut name} Atrybut  
  
| Wartość | Opis |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | Lokalizacja schematu, typy zawartości. |
  
### <a name="child-elements"></a>Elementy podrzędne  
 `Types` Element może zawierać dowolną liczbę `Default` elementów.  
  
|Element|Opis|  
|-------------|-----------------|  
|`Default`|Opisuje typ zawartości w pakiecie VSIX. Każdy typ pliku do pakietu musi mieć swój własny `Default` elementu.|  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Extension`|Rozszerzenie nazwy pliku plików w pakiecie VSIX.|  
|`ContentType`|Opisuje typ zawartości skojarzonej z rozszerzeniem nazwy pliku.|  
  
### <a name="attribute-name-attribute"></a>{Atrybut name} Atrybut  
 Program Visual Studio rozpoznaje następujące `ContentType` wartości skojarzonych z nim `Extension` typów.  
  
|Wewnętrzny|Typ zawartości|  
|---------------|-----------------|  
|txt|zwykły tekst|  
|pkgdef|zwykły tekst|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm i html|text/html|  
|RTF|Aplikacja/rtf|  
|plik PDF|Aplikacja/pdf|  
|Obraz GIF|image/gif|  
|jpg lub jpeg|Obraz/jpg|  
|TIFF|obraz/tiff|  
|vsix|Aplikacja/zip|  
|ZIP|Aplikacja/zip|  
|biblioteki dll|application/octet-stream.|  
|wszystkie typy plików|application/octet-stream.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Następującego pliku [Content_Types] .xml w tym artykule opisano typowe pakiet VSIX.  
  
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
 [Odwołanie do schematu 1.0 rozszerzenia VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Nowy Standard do pakowania danych](http://go.microsoft.com/fwlink/?LinkID=148207)