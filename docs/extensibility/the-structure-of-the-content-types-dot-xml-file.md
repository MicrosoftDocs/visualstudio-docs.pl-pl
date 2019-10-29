---
title: Struktura pliku [Content_Types]. XML | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac250053f90d99e7db27a9862d2dc1b33fadbfb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983037"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struktura pliku [Content_types].xml
Zawiera informacje o rodzaju zawartości w pakiecie VSIX. Program Visual Studio używa pliku [Content_Types]. XML do zainstalowania pakietu, ale nie instaluje samego pliku.

> [!NOTE]
> Chociaż ten temat dotyczy tylko plików [Content_Type]. XML, które są używane w pakietach VSIX, typ pliku [Content_Types]. XML jest częścią standardu *Open Package Conventions (OPC)* . Aby uzyskać więcej informacji, zobacz [OPC: A New Standard for pakowanie danych](https://msdn.microsoft.com/magazine/cc163372.aspx) w witrynie MSDN w sieci Web.

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

| Wartość | Opis |
| - | - |
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

|rozszerzenia|contentType|
|---------------|-----------------|
|zawierającego|tekst/zwykły|
|pkgdef|tekst/zwykły|
|dokument|tekst/XML|
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

## <a name="see-also"></a>Zobacz także
- [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Dokumentacja schematu rozszerzenia VSIX 1,0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: nowy standard tworzenia pakietów danych](https://msdn.microsoft.com/magazine/cc163372.aspx)