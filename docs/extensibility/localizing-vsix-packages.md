---
title: Lokalizowanie pakietów VSIX | Dokumenty firmy Microsoft
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702897"
---
# <a name="localizing-vsix-packages"></a>Lokalizowanie pakietów VSIX

Pakiet VSIX można zlokalizować, tworząc plik *Extension.vsixlangpack* dla każdego języka docelowego, a następnie umieszczając go w odpowiednim folderze. Po zainstalowaniu zlokalizowanego pakietu zlokalizowana nazwa rozszerzenia jest wyświetlana wraz z zlokalizowanym opisem. Jeśli podasz zlokalizowany plik licencji lub adres URL, który wskazuje zlokalizowane informacje, są one również wyświetlane.

Jeśli zawartość pakietu VSIX zawiera VSPackage, który dodaje polecenia menu lub inny interfejs użytkownika, zobacz [Lokalizuj polecenia menu,](../extensibility/localizing-menu-commands.md) aby uzyskać informacje na temat lokalizacji nowych elementów interfejsu użytkownika.

## <a name="directory-structure"></a>Struktura katalogów

 Gdy użytkownik instaluje rozszerzenie, **rozszerzenia i aktualizacje** sprawdza najwyższy poziom pakietu VSIX dla folderu, którego nazwa pasuje do ustawień regionalnych programu Visual Studio komputera docelowego. Jeśli **rozszerzenia i aktualizacje** znajdzie plik *vsixlangpack* w folderze, zastępuje zlokalizowane wartości w tym pliku dla odpowiednich wartości w pliku *vsixmanifest.* Wartości te są wyświetlane podczas instalowania rozszerzenia. W poniższym przykładzie przedstawiono strukturę katalogów pakietu VSIX, który jest zlokalizowany w języku hiszpańskim (es-ES) i francuskim (fr-FR).

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Szablony projektów obsługiwane przez usługę [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSIX w manifeście vsix i nazwaniu go *source.extension.vsixmanifest*. Gdy program Visual Studio tworzy projekt, kopiuje zawartość tego pliku do Extension.VsixManifest w pakiecie VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Plik Extension.vsixlangpack

Plik *Extension.vsixlangpack* jest zgodny ze [schematem 2.0 pakietu językowego VSIX](../extensibility/vsix-language-pack-schema-2-0-reference.md). Ten schemat ma `PackageLanguagePackManifest`, który jest `Metadata` natychmiast następuje element podrzędny. Element Metadane może zawierać maksymalnie 6 `Description` `MoreInfo`elementów podrzędnych, `License` `DisplayName`, , , `ReleaseNotes`, i `Icon`. Te elementy podrzędne `DisplayName` `Description`odpowiadają `MoreInfo` `License` `Metadata` elementom `Icon` elementu `ReleaseNotes` *Extension.vsixmanifest elementu Extension.vsixmanifest.*

Podczas tworzenia pliku vsixlangpack należy ustawić `Include in Vsix` właściwość na `true`. W przeciwnym razie zlokalizowany tekst instalacji zostanie zignorowany.

### <a name="to-set-the-include-in-vsix-property"></a>Aby ustawić właściwość Uwzględnij w programie Vsix

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik Extension.vsixlangpack, a następnie kliknij polecenie **Właściwości**.

2. W **siatce właściwości**kliknij pozycję **Uwzględnij w programie Vsix**i ustaw jego wartość na `true`.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie przedstawiono istotne fragmenty pliku *Extension.vsixmanifest.* Plik zawiera również odpowiedni plik *Extension.vsixlangpack* dla języka hiszpańskiego. Wartości z pakietu językowego zastępują wartości z manifestu, jeśli ustawienia regionalne programu Visual Studio komputera docelowego są ustawione na hiszpański.

### <a name="code"></a>Code

- [*Extension.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension.vsixlangpack*]

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
|[Odwołanie do schematu 2.0 pakietu językowego VSIX](vsix-language-pack-schema-2-0-reference.md)|Pakiet językowy VSIX opisuje informacje o lokalizacji pliku wdrażania vsix.|
|[Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Opisuje strukturę i zawartość pakietu vsix.|
|[Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md)|Pokazuje, jak zlokalizować inne zasoby tekstowe w rozszerzeniu.|
