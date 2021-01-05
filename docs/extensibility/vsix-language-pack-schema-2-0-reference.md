---
title: Pakiet językowy VSIX schemat 2,0 Dokumentacja | Microsoft Docs
description: Schemat pakietu Language Pack VSIX zawiera zlokalizowane informacje o instalacji pakietów VSIX. Wersja 2,0 obsługuje dodatkowe elementy lokalizacji.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: acangialosi
ms.author: anthc
manager: jillfra
ms.openlocfilehash: fc9c3c1aa7f8cf77ebf165a3e10a67ccbd5887f7
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863829"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Dokumentacja schematu pakietu języka VSIX 2,0

Schemat pakietu Language Pack VSIX zawiera zlokalizowane informacje o instalacji pakietów VSIX. Wersja 2,0 tego schematu obsługuje dodatkowe elementy lokalizacji.

## <a name="language-pack-schema"></a>Schemat pakietu językowego

Element główny pliku pakietu językowego ma `<PackageLanguagePackManifest>` atrybut `Version` , który jest wersją formatu pakietu językowego. W tym artykule opisano wersję 2,0 formatu pakietu językowego, która jest określona w manifeście przez ustawienie `Version` atrybutu na wartość `Version="2.0.0"` . Element główny zawiera dokładnie jeden element podrzędny `<Metadata>` .

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest, element

W `<PackageLanguagePackManifest>` elemencie musi istnieć następujący element:

|Tytuł|Opis|
|-----------|-----------------|
|`<Metadata>`| Element zawierający dla wszystkich zlokalizowanych metadanych pakietu

### <a name="metadata-element"></a>Element metadanych

W obrębie `<Metadata>` elementu można mieć następujące elementy:

|Tytuł|Opis|
|-----------|-----------------|
|`<DisplayName>`|Zlokalizowana nazwa rozszerzenia, które ma zostać zainstalowane|
|`<Description>`|Zlokalizowany opis rozszerzenia, które ma zostać zainstalowane|
|`<License>`| Ścieżka do zlokalizowanej wersji licencji rozszerzenia|
|`<MoreInfo>`| Link do zlokalizowanych informacji o rozszerzeniu|
|`<ReleaseNotes>`| Ścieżka lub link do zlokalizowanej wersji informacji o wersji|
|`<Icon>`| Ścieżka do zlokalizowanej wersji ikony rozszerzeń|

### <a name="sample-manifest"></a>Przykładowy manifest

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Zobacz też

|Tytuł|Opis|
|-----------|-----------------|
|[Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)|Pokazuje, jak zapewnić zlokalizowaną obsługę instalacji pakietu VSIX.|
|[Dokumentacja schematu rozszerzenia VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)|Manifest VSIX opisuje zawartość pliku wdrożenia *. vsix* . Plik wdrożenia umożliwia zainstalowanie rozszerzenia programu Visual Studio przy użyciu okna dialogowego **rozszerzenia i aktualizacje** .|
|[Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Pokazuje, w jaki sposób używać okna dialogowego **rozszerzenia i aktualizacje** do instalowania, usuwania, uaktywniania i dezaktywowania rozszerzeń.|
