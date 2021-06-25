---
title: Struktura pliku [Content_types].xml file | Microsoft Docs
description: Dowiedz się więcej o strukturze pliku typów zawartości, który zawiera informacje o rodzajach zawartości w pakiecie VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96d4d0eeea34300894674a2105d080e8a6abb607
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900424"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struktura pliku [Content_types].xml
Zawiera informacje o rodzajach zawartości w pakiecie VSIX. Visual Studio używa pliku [Content_Types].xml do zainstalowania pakietu, ale nie instaluje samego pliku.

> [!NOTE]
> Chociaż ten temat dotyczy tylko plików [Content_Type].xml używanych w pakietach VSIX, typ pliku [Content_Types].xml jest częścią standardu *Open Packaging Conventions (OPC).* Aby uzyskać więcej informacji, zobacz [OPC: A New Standard For Packaging Your Data (OPC: nowy standard](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) pakowania danych) w witrynie internetowej MSDN.

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano element główny i jego atrybuty oraz elementy podrzędne.

### <a name="root-element"></a>Root, element

|Element|Opis|
|-------------|-----------------|
|`Types`|Zawiera elementy podrzędne, które wyliczają typy plików w pakiecie VSIX.|

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Xmlns`|(Wymagane). Lokalizacja schematu używanego dla tego [Content_Types].xml pliku.|

### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Atrybut

| Wartość | Opis |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Lokalizacja schematu typów zawartości. |

### <a name="child-elements"></a>Elementy podrzędne
 Element `Types` może zawierać dowolną liczbę `Default` elementów.

|Element|Opis|
|-------------|-----------------|
|`Default`|Opisuje typ zawartości w pakiecie VSIX. Każdy typ pliku w pakiecie musi mieć własny `Default` element.|

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Extension`|Rozszerzenie nazwy pliku w pakiecie VSIX.|
|`ContentType`|Opisuje rodzaj zawartości, która jest skojarzona z rozszerzeniem nazwy pliku.|

### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Atrybut
 Visual Studio rozpoznaje następujące wartości `ContentType` dla skojarzonych `Extension` typów.

|Wewnętrzny|Contenttype|
|---------------|-----------------|
|Txt|tekst/zwykły|
|pkgdef|tekst/zwykły|
|xml|text/xml|
|Vsixmanifest|text/xml|
|htm lub html|text/html|
|Rtf|application/rtf|
|pdf|application/pdf|
|Gif|image/gif|
|jpg lub jpeg|image/jpg|
|tiff|image/tiff|
|vsix|aplikacja/zip|
|Zip|aplikacja/zip|
|Dll|application/octet-stream|
|wszystkie inne typy plików|application/octet-stream|

## <a name="example"></a>Przykład

### <a name="description"></a>Opis
 Poniższy plik [Content_Types].xml opisuje typowy pakiet VSIX.

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
- [Odwołanie do schematu 1.0 rozszerzenia VSIX](/previous-versions/dd393700(v=vs.110))
- [OPC: nowy standard pakowania danych](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)