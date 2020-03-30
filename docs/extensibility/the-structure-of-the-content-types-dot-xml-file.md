---
title: Struktura pliku [Content_types].xml | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 957958cd930620734d09c592ea07bfb0919d0145
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395308"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struktura pliku [Content_types].xml
Zawiera informacje o rodzajach zawartości w pakiecie VSIX. Program Visual Studio używa [Content_Types].xml pliku, aby zainstalować pakiet, ale nie instaluje samego pliku.

> [!NOTE]
> Chociaż ten temat dotyczy tylko plików [Content_Type].xml, które są używane w pakietach VSIX, [Content_Types].xml typ pliku jest częścią *standardu Open Packaging Conventions (OPC).* Aby uzyskać więcej informacji, zobacz [OPC: A New Standard For Packaging Your Data](https://msdn.microsoft.com/magazine/cc163372.aspx) on the MSDN Web site.

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano element główny i jego atrybuty i elementy podrzędne.

### <a name="root-element"></a>Element główny

|Element|Opis|
|-------------|-----------------|
|`Types`|Zawiera elementy podrzędne, które wyliczają typy plików w pakiecie VSIX.|

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Xmlns`|(Wymagane). Lokalizacja schematu używanego dla tego pliku [Content_Types].xml.|

### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Atrybut

| Wartość | Opis |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Lokalizacja schematu typów zawartości. |

### <a name="child-elements"></a>Elementy podrzędne
 Element `Types` może zawierać dowolną `Default` liczbę elementów.

|Element|Opis|
|-------------|-----------------|
|`Default`|Opisuje typ zawartości w pakiecie VSIX. Każdy typ pliku w pakiecie `Default` musi mieć swój własny element.|

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Extension`|Rozszerzenie nazwy pliku w pakiecie VSIX.|
|`ContentType`|Opisuje rodzaj zawartości skojarzonej z rozszerzeniem nazwy pliku.|

### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Atrybut
 Visual Studio rozpoznaje `ContentType` następujące wartości `Extension` dla skojarzonych typów.

|Wewnętrzny|Contenttype|
|---------------|-----------------|
|Txt|tekst/zwykły|
|pkgdef (własob)|tekst/zwykły|
|xml|tekst/xml|
|Vsixmanifest|tekst/xml|
|htm lub html|text/html|
|Rtf|aplikacja/rtf|
|pdf|aplikacja/pdf|
|Gif|obraz/gif|
|jpg lub jpeg|obraz/jpg|
|tiff|obraz/tiff|
|vsix|aplikacja/zamek błyskawiczny|
|Zip|aplikacja/zamek błyskawiczny|
|Dll|aplikacja/oktet-strumień|
|wszystkie inne typy plików|aplikacja/oktet-strumień|

## <a name="example"></a>Przykład

### <a name="description"></a>Opis
 Poniżej [Content_Types].xml plik opisuje typowy pakiet VSIX.

### <a name="code"></a>Code

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
- [Odwołanie do schematu rozszerzenia VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: Nowy standard pakowania danych](https://msdn.microsoft.com/magazine/cc163372.aspx)