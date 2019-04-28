---
title: VSIX Language Pack — dokumentacja schematu 2.0 | Dokumentacja firmy Microsoft
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: jillfra
ms.workload:
- dagriffe
ms.openlocfilehash: acea36031b98693e1d618986720d9932f76a0a63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953104"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX language pack — dokumentacja schematu 2.0

Schemat pakietu językowego VSIX informacje zlokalizowanej instalację pakietów VSIX. W wersji 2.0 tego schematu obsługuje elementy dodatkowej lokalizacji.

## <a name="language-pack-schema"></a>Schemat pakiet języka

Element główny pliku pakiet języka jest `<PackageLanguagePackManifest>`, z atrybutem `Version`, czyli wersji formatu pakietu języka. W tym artykule opisano w wersji 2.0 formatu pakietu języka, który jest określany w manifeście przez ustawienie `Version` atrybut na wartość `Version="2.0.0"`. Element główny zawiera dokładnie jeden element podrzędny `<Metadata>` elementu.

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest element

W ramach `<PackageLanguagePackManifest>` element musi istnieć następującego elementu:

|Tytuł|Opis|
|-----------|-----------------|
|`<Metadata>`| Element zawierający dla wszystkich metadanych zlokalizowanego pakietu

### <a name="metadata-element"></a>Element metadanych

W ramach `<Metadata>` element może mieć następujące elementy:

|Tytuł|Opis|
|-----------|-----------------|
|`<DisplayName>`|Zlokalizowana nazwa rozszerzenia do zainstalowania|
|`<Description>`|Zlokalizowany opis rozszerzenia do zainstalowania|
|`<License>`| Ścieżka do zlokalizowaną wersję licencji rozszerzenia|
|`<MoreInfo>`| Link do zlokalizowanych informacji o rozszerzeniu|
|`<ReleaseNotes>`| Ścieżka lub link do zlokalizowaną wersję informacje o wersji|
|`<Icon>`| Ścieżka do zlokalizowaną wersję ikonę rozszerzenia|

### <a name="sample-manifest"></a>Manifest próbki

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
|[Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)|Pokazuje, jak do obsługi zlokalizowanej instalację pakietu VSIX.|
|[Odwołanie do schematu 2.0 rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX manifest w tym artykule opisano zawartość *.vsix* pliku wdrożenia. Plik wdrożenia umożliwia zainstalowanie rozszerzenia programu Visual Studio przy użyciu **rozszerzenia i aktualizacje** okno dialogowe.|
|[Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Ilustruje sposób używania **rozszerzenia i aktualizacje** okno dialogowe instalowanie, usuwanie, włączanie i wyłączanie rozszerzenia.|