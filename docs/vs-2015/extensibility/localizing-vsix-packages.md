---
title: Lokalizowanie pakietów VSIX | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e370f48559638e8c68ea5ac8e04eca6960983475
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046089"
---
# <a name="localizing-vsix-packages"></a>Lokalizowanie pakietów VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można lokalizować pakiet VSIX przez utworzenie pliku Extension.vsixlangpack dla każdego języka docelowego i umieszczenie ich w odpowiednim folderze. Po zainstalowaniu pakietu zlokalizowane zlokalizowana nazwa rozszerzenia jest wyświetlana wraz z zlokalizowanym opisem. Jeśli podasz pliku zlokalizowanego licencji lub adres URL, który wskazuje na zlokalizowane informacje są także wyświetlane.  
  
 Jeśli zawartość pakietu VSIX zawiera pakietu VSPackage, który dodaje poleceń menu lub innego interfejsu użytkownika, zapoznaj się z [lokalizowanie poleceń Menu](../extensibility/localizing-menu-commands.md) uzyskać informacji na temat lokalizowanie nowych elementów interfejsu użytkownika.  
  
## <a name="directory-structure"></a>Struktura katalogów  
 Gdy użytkownik instaluje rozszerzenie **rozszerzenia i aktualizacje** sprawdza najwyższym poziomie pakietu VSIX do folderu, w których nazwa jest zgodna z ustawieniami regionalnymi programu Visual Studio na komputerze docelowym. Jeśli **rozszerzenia i aktualizacje** napotka .vsixlangpack plików w folderze, zastępuje zlokalizowane wartości w tym pliku, aby uzyskać odpowiednie wartości w pliku .vsixmanifest. Te wartości są wyświetlane po zainstalowaniu rozszerzenia. Poniższy przykład pokazuje strukturę katalogu pakietu VSIX, który jest zlokalizowany w hiszpański (es-ES) i francuski (fr-FR).  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types] .xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Szablony projektu VSIX, obsługiwane w [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] generowania manifestu VSIX i nadaj mu nazwę source.extension.vsixmanifest. Gdy program Visual Studio tworzy projekt, kopiuje zawartość tego pliku do Extension.VsixManifest w pakiecie VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Plik Extension.vsixlangpack  
 Plik Extension.vsixlangpack [VSIX Language Pack schematu](../extensibility/vsx-language-pack-schema-reference.md). Ten schemat zawiera [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) element główny i te elementy podrzędne cztery: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), i [licencji](../extensibility/license-element-vsix-language-pack-schema.md). Te elementy podrzędne odpowiadają `Name`, `Description`, `MoreInfoURL`, i `License` elementów podrzędnych `Identifier` element pliku Extension.vsixmanifest.  
  
 Podczas tworzenia pliku vsixlangpack należy ustawić `Include in Vsix` właściwość `true`. W przeciwnym razie tekst zlokalizowanej instalację zostaną zignorowane.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Aby ustawić dołączania we właściwości Vsix  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Extension.vsixlangpack, a następnie kliknij **właściwości**.  
  
2. W siatce właściwości kliknij **Include w Vsix**i ustaw jej wartość na `true`.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy kod przedstawia istotne części pliku Extension.vsixmanifest wraz z odpowiedniego pliku Extension.vsixlangpack dla języka hiszpańskiego. Wartości z pakietu językowego należy zastąpić wartości z manifestu, jeśli ustawienia regionalne programu Visual Studio na komputerze docelowym jest ustawiony na język hiszpański.  
  
### <a name="code"></a>Kod  
 [Extension.vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Element pakietu językowego VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Szablon projektu VSIX](../extensibility/vsix-project-template.md)
