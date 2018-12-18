---
title: Struktura Content_types] .xml pliku | Dokumentacja firmy Microsoft
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
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5892ab545c41f7d58f0d097f3d27c90c090f0ff
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736574"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Struktura Content_types] .xml pliku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera informacje na temat rodzajów zawartości w pakiecie VSIX. Program Visual Studio używa pliku [Content_Types] .xml, aby zainstalować pakiet, ale nie jest instalowana w samym pliku.  
  
> [!NOTE]
>  Mimo że w tym temacie mają zastosowanie tylko do plików XML [Content_Type], które są używane w pakietów VSIX, typu pliku [Content_Types] .xml jest częścią *otwarte konwencje tworzenia pakietów (OPC)* standardowych. Aby uzyskać więcej informacji, zobacz [OPC: nowy Standard do pakowania własnych danych](http://go.microsoft.com/fwlink/?LinkID=148207) w witrynie MSDN w sieci Web.  
  
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
  
|                           Wartość                           |                Opis                |
|-----------------------------------------------------------|-------------------------------------------|
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
  
|Rozszerzenie|Typ zawartości|  
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
 [Odwołanie do schematu 1.0 rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Nowy Standard do pakowania danych](http://go.microsoft.com/fwlink/?LinkID=148207)

