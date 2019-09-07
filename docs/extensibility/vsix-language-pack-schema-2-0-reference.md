---
title: Pakiet językowy VSIX schemat 2,0 Dokumentacja | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: zorio
author: zoeyr
manager: jillfra
ms.openlocfilehash: fe6d4bd9e82950d77925dda1560b5c204633d392
ms.sourcegitcommit: dae5dfd626277b58ebd7b21a75757f683f1eacc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739333"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Dokumentacja schematu pakietu języka VSIX 2,0

Schemat pakietu Language Pack VSIX zawiera zlokalizowane informacje o instalacji pakietów VSIX. Wersja 2,0 tego schematu obsługuje dodatkowe elementy lokalizacji.

## <a name="language-pack-schema"></a>Schemat pakietu językowego

Element główny pliku pakietu językowego ma `<PackageLanguagePackManifest>` `Version`atrybut, który jest wersją formatu pakietu językowego. W tym artykule opisano wersję 2,0 formatu pakietu językowego, która jest określona w manifeście przez ustawienie `Version` atrybutu na wartość. `Version="2.0.0"` Element główny zawiera dokładnie jeden element podrzędny `<Metadata>` .

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest, element

`<PackageLanguagePackManifest>` W elemencie musi istnieć następujący element:

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
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Zobacz także

|Tytuł|Opis|
|-----------|-----------------|
|[Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)|Pokazuje, jak zapewnić zlokalizowaną obsługę instalacji pakietu VSIX.|
|[Dokumentacja schematu rozszerzenia VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)|Manifest VSIX opisuje zawartość pliku wdrożenia *. vsix* . Plik wdrożenia umożliwia zainstalowanie rozszerzenia programu Visual Studio przy użyciu okna dialogowego **rozszerzenia i aktualizacje** .|
|[Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Pokazuje, w jaki sposób używać okna dialogowego **rozszerzenia i aktualizacje** do instalowania, usuwania, uaktywniania i dezaktywowania rozszerzeń.|
