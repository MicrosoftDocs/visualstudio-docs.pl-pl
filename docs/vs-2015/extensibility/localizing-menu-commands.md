---
title: Lokalizowanie poleceń Menu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27be664fb035af2c97f0536026b590c468b68b9e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771423"
---
# <a name="localizing-menu-commands"></a>Lokalizowanie poleceń menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz podać zlokalizowany tekst menu i paska narzędzi poleceń, tworząc zlokalizowane .vsct — pliki i zlokalizowane pliki resx dla Twojego pakietu VSPackage, a następnie zaktualizować plików projektu wprowadzić zmiany.  
  
 Aby uzyskać informacje o sposobie lokalizowania środowisko instalacji, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Lokalizowanie nazw poleceń  
 W pakietach VSPackage polecenia menu i przycisków na pasku narzędzi są definiowane w pliku vsct.  
  
1. W **Eksploratora rozwiązań**, Zmień nazwę pliku vsct z *filename*vsct do *filename*.en US.vsct.  
  
2. Utwórz kopię *filename*.en-US.vsct dla każdego zlokalizowanego języka.  
  
    Nazwy poszczególnych kopii *filename*. *Ustawienia regionalne*vsct, gdzie *ustawień regionalnych* jest nazwą określonej kultury. Aby uzyskać listę wartości nazwy kultury, zobacz [identyfikatory ustawień regionalnych przypisane przez firmę Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Te *filename*. *Ustawienia regionalne*.vsct — pliki będzie zawierać tekst menu zlokalizowanego pakietu.  
  
3. Otwórz każdy *filename*. *Ustawienia regionalne*pliku vsct do zlokalizowania tekstu.  
  
   1. Modyfikowanie [ButtonText](../extensibility/buttontext-element.md) element wartości odpowiednie dla danego języka.  
  
   2. Jeśli podasz zlokalizowane ikony, należy zmodyfikować [mapy bitowej](../extensibility/bitmap-element.md) wartości, aby wskazywały pliki docelowe.  
  
      Poniższy przykład pokazuje języków angielskiego i hiszpańskiego tekst przycisku polecenia otworzyć okno narzędzia z rodziny drzewa Eksploratora.  
  
      [FamilyTree.en US.vsct]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Family Tree Explorer</ButtonText>  
     </Strings>  
   </Button>  
   ```  
  
    [FamilyTree.es-ES.vsct]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Explorar el arbol genealogico</ButtonText>  
     </Strings>  
   </Button>  
  
   ```  
  
## <a name="localizing-other-text-resources"></a>Lokalizowanie inne zasoby tekstu  
 Tekst zasobów innych niż nazw poleceń są zdefiniowane w plikach źródłowych (resx).  
  
1.  Zmień nazwę VSPackage.resx VSPackage.en US.resx.  
  
2.  Utwórz kopię pliku VSPackage.en US.resx dla każdego lokalizowanego języka.  
  
     Nazwa każdej kopii pakietu VSPackage. *Ustawień regionalnych*resx, gdzie *ustawień regionalnych* jest nazwą określonej kultury.  
  
3.  Zmień nazwę Resources.en US.resx Resources.resx.  
  
4.  Utwórz kopię pliku Resources.en US.resx dla każdego lokalizowanego języka.  
  
     Nazwa każdej kopii zasobów. *Ustawień regionalnych*resx, gdzie *ustawień regionalnych* jest nazwą określonej kultury.  
  
5.  Otwórz każdy plik Resx, aby zmodyfikować wartości ciągu, zgodnie z potrzebami dla określonego języka i kultury. Poniższy przykład przedstawia definicję zlokalizowanych zasobów, na pasku tytułu okna narzędzi.  
  
     [Resources.en-US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Dołączanie zlokalizowane zasoby do projektu  
 Należy zmodyfikować plik assemblyinfo.cs i pliku projektu, aby dołączyć zlokalizowanych zasobów.  
  
1.  Z **właściwości** w węźle **Eksploratora rozwiązań**, otwórz assemblyinfo.cs lub assemblyinfo.vb w edytorze.  
  
2.  Dodaj następujący wpis.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Spowoduje to ustawienie US English jako domyślny język.  
  
3.  Zwolnij projekt.  
  
4.  Otwórz plik projektu w edytorze.  
  
5.  Znajdź `ItemGroup` element, który zawiera `EmbeddedResource` elementów.  
  
6.  W `EmbeddedResource` Zastąp element, który wywołuje VSPackage.en-US.resx `ManifestResourceName` element z `LogicalName` elementu, ustaw `VSPackage.en-US.Resources`, wykonując następujące czynności.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Dla każdego lokalizowanego języka Skopiuj `EmbeddedResource` elementu VsPackage.en USA oraz zestaw **Include** atrybutu i **LogicalName** element Kopiuj do docelowych ustawień regionalnych, jak pokazano w poniższym przykład.  
  
8.  Dla każdego zlokalizowanego `VSCTCompile` elementu Dodawanie `ResourceName` element, który wskazuje na `Menus.ctmenu`, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Zapisz plik projektu i ponownie Załaduj projekt.  
  
10. Skompiluj projekt.  
  
     Spowoduje to utworzenie w głównym zestawie i zestawów zasobów dla każdego języka. Aby uzyskać informacji na temat lokalizowanie proces wdrażania, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands programu Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalizacja i lokalizacja](http://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
