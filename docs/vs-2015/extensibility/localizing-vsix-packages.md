---
title: Lokalizowanie pakietów VSIX | Microsoft Docs
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
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795207"
---
# <a name="localizing-vsix-packages"></a>Lokalizowanie pakietów VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakiet VSIX można zlokalizować przez utworzenie pliku Extension. vsixlangpack dla każdego języka docelowego, a następnie umieszczenie ich we właściwym folderze. Gdy zlokalizowany pakiet jest zainstalowany, zlokalizowana nazwa rozszerzenia jest wyświetlana wraz z zlokalizowanym opisem. Jeśli podasz zlokalizowany plik licencji lub adres URL wskazujący zlokalizowane informacje, są one również wyświetlane.  
  
 Jeśli zawartość pakietu VSIX zawiera pakietu VSPackage, który dodaje polecenia menu lub inny interfejs użytkownika, zobacz [lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md) , aby uzyskać informacje dotyczące lokalizowania nowych elementów interfejsu użytkownika.  
  
## <a name="directory-structure"></a>Struktura katalogów  
 Gdy użytkownik instaluje rozszerzenie, **rozszerzenia i aktualizacje** sprawdza najwyższy poziom pakietu VSIX dla folderu, którego nazwa pasuje do ustawień regionalnych programu Visual Studio na komputerze docelowym. Jeśli **rozszerzenia i aktualizacje** znajdą plik. vsixlangpack w folderze, zastępuje zlokalizowane wartości w tym pliku dla odpowiednich wartości w pliku. vsixmanifest. Te wartości są wyświetlane podczas instalowania rozszerzenia. W poniższym przykładzie pokazano strukturę katalogów pakietu VSIX zlokalizowanego w języku hiszpańskim (es-ES) i francuskim (fr-FR).  
  
 MyExtension.dll  
  
 Rozszerzenie. vsixmanifest  
  
 [Content_Types]. XML  
  
 es-ES  
  
 Rozszerzenie. vsixlangpack  
  
 fr-FR  
  
 Rozszerzenie. vsixlangpack  
  
> [!NOTE]
> Szablony projektów obsługiwane przez VSIX w pliku [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Generuj manifest VSIX i nadaj mu nazwę source. Extension. vsixmanifest. Gdy program Visual Studio kompiluje projekt, kopiuje zawartość tego pliku do Extension. VsixManifest w pakiecie VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Plik rozszerzenia. vsixlangpack  
 Plik Extension. vsixlangpack jest zgodny ze [schematem pakietu Language Pack VSIX](../extensibility/vsx-language-pack-schema-reference.md). Ten schemat zawiera element główny [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) oraz te cztery elementy podrzędne: [lokalizowaćname](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)i [License](../extensibility/license-element-vsix-language-pack-schema.md). Te elementy podrzędne odpowiadają `Name` `Description` `MoreInfoURL` elementom,, i `License` potomnym `Identifier` elementu pliku Extension. vsixmanifest.  
  
 Podczas tworzenia pliku vsixlangpack należy ustawić `Include in Vsix` Właściwość na `true` . W przeciwnym razie zlokalizowany tekst instalacji zostanie zignorowany.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Aby ustawić właściwość include w VSIX  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik Extension. vsixlangpack, a następnie kliknij polecenie **Właściwości**.  
  
2. W siatce właściwości kliknij pozycję **Dołącz w VSIX**i ustaw jej wartość na `true` .  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono odpowiednie fragmenty pliku Extension. vsixmanifest wraz z odpowiednim plikiem Extension. vsixlangpack dla języka hiszpańskiego. Wartości z pakietu językowego zastępują wartości z manifestu, jeśli ustawienia regionalne programu Visual Studio na komputerze docelowym zostały ustawione na hiszpański.  
  
### <a name="code"></a>Kod  
 [Extension. vsixmanifest]  
  
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
  
 [Extension. vsixlangpack]  
  
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
 [VSIX — element LanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Szablon projektu VSIX](../extensibility/vsix-project-template.md)
