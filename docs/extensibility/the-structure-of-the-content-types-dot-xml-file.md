---
title: Struktura pliku [Content_types]. XML | Microsoft Docs
description: Dowiedz się więcej na temat struktury pliku typów zawartości, który zawiera informacje o rodzaju zawartości w pakiecie VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7117845e4756f8b0e09a8fa603e66448e705b903
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715226"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struktura pliku [Content_types].xml
Zawiera informacje o rodzaju zawartości w pakiecie VSIX. Program Visual Studio używa pliku XML [Content_Types] do zainstalowania pakietu, ale nie instaluje samego pliku.

> [!NOTE]
> Chociaż ten temat dotyczy tylko plików [Content_Type]. XML, które są używane w pakietach VSIX, typ pliku [Content_Types]. XML jest częścią standardu *Open Package Conventions (OPC)* . Aby uzyskać więcej informacji, zobacz [OPC: A New Standard for pakowanie danych](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) w witrynie MSDN w sieci Web.

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
| `http://schemas.openformats.org/package/2006/content-types` | Lokalizacja schematu typów zawartości. |

### <a name="child-elements"></a>Elementy podrzędne
 `Types`Element może zawierać dowolną liczbę `Default` elementów.

|Element|Opis|
|-------------|-----------------|
|`Default`|Opisuje typ zawartości w pakiecie VSIX. Każdy typ pliku w pakiecie musi mieć własny `Default` element.|

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Extension`|Rozszerzenie nazwy pliku w pakiecie VSIX.|
|`ContentType`|Opisuje rodzaj zawartości skojarzonej z rozszerzeniem nazwy pliku.|

### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Przypisane
 Program Visual Studio rozpoznaje następujące `ContentType` wartości dla skojarzonych `Extension` typów.

|Wewnętrzny|ContentType|
|---------------|-----------------|
|zawierającego|tekst/zwykły|
|pkgdef|tekst/zwykły|
|xml|tekst/XML|
|vsixmanifest|tekst/XML|
|htm lub HTML|text/html|
|RTF|Aplikacja/RTF|
|pdf|Aplikacja/plik PDF|
|GIF|obraz/GIF|
|jpg lub JPEG|obraz/jpg|
|tiff|obraz/TIFF|
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
- [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Dokumentacja schematu rozszerzenia VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [OPC: nowy standard tworzenia pakietów danych](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)