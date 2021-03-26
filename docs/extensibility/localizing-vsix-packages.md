---
title: Lokalizowanie pakietów VSIX | Microsoft Docs
description: Dowiedz się, jak lokalizować pakiet VSIX, tworząc plik rozszerzenia vsixlangpack dla każdego języka docelowego, a następnie umieszczając je w prawidłowym folderze.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d2e297484e89f1ae2cfb9f2be7af25f1fe92714
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073225"
---
# <a name="localizing-vsix-packages"></a>Lokalizowanie pakietów VSIX

Pakiet VSIX można zlokalizować przez utworzenie pliku *Extension. vsixlangpack* dla każdego języka docelowego, a następnie umieszczenie ich we właściwym folderze. Gdy zlokalizowany pakiet jest zainstalowany, zlokalizowana nazwa rozszerzenia jest wyświetlana wraz z zlokalizowanym opisem. Jeśli podasz zlokalizowany plik licencji lub adres URL wskazujący zlokalizowane informacje, są one również wyświetlane.

Jeśli zawartość pakietu VSIX zawiera pakietu VSPackage, który dodaje polecenia menu lub inny interfejs użytkownika, zobacz [lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md) , aby uzyskać informacje na temat lokalizowania nowych elementów interfejsu użytkownika.

## <a name="directory-structure"></a>Struktura katalogów

 Gdy użytkownik instaluje rozszerzenie, **rozszerzenia i aktualizacje** sprawdza najwyższy poziom pakietu VSIX dla folderu, którego nazwa pasuje do ustawień regionalnych programu Visual Studio na komputerze docelowym. Jeśli **rozszerzenia i aktualizacje** znajdą plik *. vsixlangpack* w folderze, zastępuje zlokalizowane wartości w tym pliku dla odpowiednich wartości w pliku *. vsixmanifest* . Te wartości są wyświetlane podczas instalowania rozszerzenia. W poniższym przykładzie pokazano strukturę katalogów pakietu VSIX zlokalizowanego w języku hiszpańskim (es-ES) i francuskim (fr-FR).

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
> Szablony projektów obsługiwane przez VSIX w pliku [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Generuj manifest VSIX i nadaj mu nazwę *source. Extension. vsixmanifest*. Gdy program Visual Studio kompiluje projekt, kopiuje zawartość tego pliku do Extension. VsixManifest w pakiecie VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Plik rozszerzenia. vsixlangpack

Plik *Extension. vsixlangpack* jest zgodny ze [schematem pakietu Language Pack VSIX 2,0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Ten schemat ma `PackageLanguagePackManifest` , który bezpośrednio następuje po `Metadata` elemencie podrzędnym. Element Metadata może zawierać do 6 elementów podrzędnych,,,,, `DisplayName` `Description` `MoreInfo` `License` `ReleaseNotes` i `Icon` . Te elementy podrzędne odpowiadają `DisplayName` `Description` `MoreInfo` elementom,,,, `License` `ReleaseNotes` i `Icon` podrzędnym `Metadata` elementu *rozszerzenia. vsixmanifest* .

Podczas tworzenia pliku vsixlangpack należy ustawić `Include in Vsix` Właściwość na `true` . W przeciwnym razie zlokalizowany tekst instalacji zostanie zignorowany.

### <a name="to-set-the-include-in-vsix-property"></a>Aby ustawić właściwość include w VSIX

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik Extension. vsixlangpack, a następnie kliknij polecenie **Właściwości**.

2. W **siatce właściwości** kliknij pozycję **Dołącz w VSIX** i ustaw jej wartość na `true` .

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład przedstawia istotne fragmenty pliku *Extension. vsixmanifest* . Plik zawiera również odpowiedni plik *Extension. vsixlangpack* dla języka hiszpańskiego. Wartości z pakietu językowego zastępują wartości z manifestu, jeśli ustawienia regionalne programu Visual Studio na komputerze docelowym zostały ustawione na hiszpański.

### <a name="code"></a>Kod

- [*Extension. vsixmanifest*]

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

- [*Extension. vsixlangpack*]

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
|[Dokumentacja schematu pakietu języka VSIX 2,0](vsix-language-pack-schema-2-0-reference.md)|Pakiet językowy VSIX zawiera opis informacji o lokalizacji pliku wdrożenia. VSIX.|
|[Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Opisuje strukturę i zawartość pakietu VSIX.|
|[Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md)|Pokazuje, jak lokalizować inne zasoby tekstowe w rozszerzeniu.|
