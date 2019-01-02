---
title: Lokalizowanie pakietów VSIX | Dokumentacja firmy Microsoft
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d554819c8c615dc9f8fcd41bb4b460482e21fde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956936"
---
# <a name="localizing-vsix-packages"></a>Lokalizowanie pakietów VSIX

Można lokalizować pakiet VSIX przez utworzenie *Extension.vsixlangpack* pliku dla każdego języka docelowego i umieszczenie ich w odpowiednim folderze. Po zainstalowaniu pakietu zlokalizowane zlokalizowana nazwa rozszerzenia jest wyświetlana wraz z zlokalizowanym opisem. Jeśli podasz pliku zlokalizowanego licencji lub adres URL, który wskazuje na zlokalizowane informacje są także wyświetlane.

Jeśli zawartość pakietu VSIX zawiera pakietu VSPackage, który dodaje poleceń menu lub innego interfejsu użytkownika, zapoznaj się z [lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md) uzyskać informacji na temat lokalizowanie nowych elementów interfejsu użytkownika.

## <a name="directory-structure"></a>Struktura katalogów

 Gdy użytkownik instaluje rozszerzenie **rozszerzenia i aktualizacje** sprawdza najwyższym poziomie pakietu VSIX do folderu, w których nazwa jest zgodna z ustawieniami regionalnymi programu Visual Studio na komputerze docelowym. Jeśli **rozszerzenia i aktualizacje** znajdzie *.vsixlangpack* pliku w folderze, zastępuje zlokalizowane wartości w tym pliku, aby uzyskać odpowiednie wartości w *.vsixmanifest*pliku. Te wartości są wyświetlane po zainstalowaniu rozszerzenia. Poniższy przykład pokazuje strukturę katalogu pakietu VSIX, który jest zlokalizowany w hiszpański (es-ES) i francuski (fr-FR).  

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
> Szablony projektu VSIX, obsługiwane w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generowania manifestu VSIX i nadaj mu nazwę *source.extension.vsixmanifest*. Gdy program Visual Studio tworzy projekt, kopiuje zawartość tego pliku do Extension.VsixManifest w pakiecie VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Plik Extension.vsixlangpack

*Extension.vsixlangpack* pliku obserwowanych [pakietu językowego VSIX schematu 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Ten schemat zawiera `PackageLanguagePackManifest`, którym bezpośrednio następuje `Metadata` elementu podrzędnego. Element metadanych może zawierać maksymalnie 6 elementów podrzędnych, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, i `Icon`. Te elementy podrzędne odpowiadają `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, i `Icon` elementów podrzędnych `Metadata` elementu *Extension.vsixmanifest*pliku.

Podczas tworzenia pliku vsixlangpack należy ustawić `Include in Vsix` właściwość `true`. W przeciwnym razie tekst zlokalizowanej instalację zostaną zignorowane.

### <a name="to-set-the-include-in-vsix-property"></a>Aby ustawić dołączania we właściwości Vsix

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Extension.vsixlangpack, a następnie kliknij **właściwości**.

2.  W **siatki właściwości**, kliknij przycisk **Include w Vsix**i ustaw jej wartość na `true`.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy kod przedstawia istotne części *Extension.vsixmanifest* pliku. Plik zawiera także odpowiednie *Extension.vsixlangpack* pliku hiszpański. Wartości z pakietu językowego należy zastąpić wartości z manifestu, jeśli ustawienia regionalne programu Visual Studio na komputerze docelowym jest ustawiony na język hiszpański.

### <a name="code"></a>Kod

 [*Extension.vsixmanifest*]

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

 [*Extension.vsixlangpack*]

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

## <a name="see-also"></a>Zobacz także

|Tytuł|Opis|
|-----------|-----------------|
|[VSIX Language Pack — dokumentacja schematu 2.0](/visualstudio/extensibility/vsix-language-pack-schema-2-0-reference)|Pakietu językowego VSIX zawiera opis informacji o lokalizacji pliku .vsix wdrożenia.|
|[Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)|W tym artykule opisano, struktury i zawartości pakietu vsix.|
|[Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md)|Pokazuje, jak zlokalizować inne zasoby tekstu w rozszerzeniu.|