---
title: Lokalizowanie poleceń Menu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 648bf8baebc8a0a2f42c69bc698d9f2edd729615
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907357"
---
# <a name="localize-menu-commands"></a>Lokalizowanie poleceń menu
Możesz podać zlokalizowanego tekstu polecenia menu i paski narzędzi, tworząc zlokalizowane *vsct* pliki i zlokalizowane *resx* plików dla Twojego pakietu VSPackage, a następnie zaktualizować plików projektu dołączyć zmiany.

 Aby uzyskać informacje o sposobie lokalizowania środowisko instalacji, zobacz [pakietów VSIX lokalizowanie](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalizowanie nazw poleceń
 W pakietach VSPackage, polecenia menu i przycisków na pasku narzędzi są definiowane w *vsct* pliku.

1. W **Eksploratora rozwiązań**, Zmień nazwę *vsct* plik wchodzącej w skład *filename.vsct* do *filename.en US.vsct*.

2. Utwórz kopię *filename.en US.vsct* dla każdego zlokalizowanego języka.

    Nazwy poszczególnych kopii *filename. { Vsct Locale}*, gdzie *{ustawienia regionalne}* jest nazwą określonej kultury. Aby uzyskać listę wartości nazwy kultury, zobacz [identyfikatory ustawień regionalnych przypisane przez firmę Microsoft](/windows/uwp/publish/supported-languages).

    Te *nazwy pliku. Locale.vsct* pliki zawierają tekst menu zlokalizowanego pakietu.

3. Otwórz każdy *nazwy pliku. Locale.vsct* pliku, aby zlokalizować tekstu.

   1. Modyfikowanie [ButtonText](../extensibility/buttontext-element.md) element wartości odpowiednie dla danego języka.

   2. Jeśli podasz zlokalizowane ikony, należy zmodyfikować [mapy bitowej](../extensibility/bitmap-element.md) wartości, aby wskazywały pliki docelowe.

      Poniższy przykład pokazuje języków angielskiego i hiszpańskiego tekst przycisku polecenia otworzyć okno narzędzia z rodziny drzewa Eksploratora.

      [*FamilyTree.en US.vsct*]

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

    [*FamilyTree.es ES.vsct*]

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

## <a name="localize-other-text-resources"></a>Lokalizowanie inne zasoby tekstu
 Tekst zasobów innych niż nazw poleceń są zdefiniowane w zasobie (*resx*) plików.

1. Zmień nazwę *VSPackage.resx* do *VSPackage.en US.resx*.

2. Utwórz kopię *VSPackage.en US.resx* pliku dla każdego zlokalizowanego języka.

     Nazwy poszczególnych kopii *pakietu VSPackage. { Ustawienia regionalne} resx*, gdzie *{ustawienia regionalne}* jest nazwą określonej kultury.

3. Zmień nazwę *Resources.resx* do *Resources.en US.resx*.

4. Utwórz kopię *Resources.en US.resx* pliku dla każdego zlokalizowanego języka.

     Nazwy poszczególnych kopii *zasobów. { Ustawienia regionalne} resx*, gdzie *{ustawienia regionalne}* jest nazwą określonej kultury.

5. Otwórz każdy *resx* pliku do zmodyfikowania ciągu wartości odpowiednie dla danego języka i kultury. Poniższy przykład przedstawia definicję zlokalizowanych zasobów, na pasku tytułu okna narzędzi.

     [*Resources.en US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>

    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Włączenie zlokalizowane zasoby do projektu
 Należy zmodyfikować *assemblyinfo.cs* plików i pliku projektu, aby dołączyć zlokalizowanych zasobów.

1. Z **właściwości** w węźle **Eksploratora rozwiązań**, otwórz *assemblyinfo.cs* lub *assemblyinfo.vb* w edytorze.

2. Dodaj następujący wpis.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Spowoduje to ustawienie US English jako domyślny język.

3. Zwolnij projekt.

4. Otwórz plik projektu w edytorze.

5. Znajdź `ItemGroup` element, który zawiera `EmbeddedResource` elementów.

6. W `EmbeddedResource` element, który wywołuje *VSPackage.en US.resx*, Zastąp `ManifestResourceName` element z `LogicalName` elementu, ustaw `VSPackage.en-US.Resources`, wykonując następujące czynności.

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

7. Dla każdego lokalizowanego języka Skopiuj `EmbeddedResource` elementu `VsPackage.en-US`i ustaw **Include** atrybutu i **LogicalName** element Kopiuj do docelowych ustawień regionalnych, jak pokazano w poniższym przykład.

8. Dla każdego zlokalizowanego `VSCTCompile` elementu Dodawanie `ResourceName` element, który wskazuje na `Menus.ctmenu`, jak pokazano w poniższym przykładzie.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

9. Zapisz plik projektu i ponownie Załaduj projekt.

10. Skompiluj projekt.

     Spowoduje to utworzenie w głównym zestawie i zestawów zasobów dla każdego języka. Aby uzyskać informacji na temat lokalizowanie proces wdrażania, zobacz [pakietów VSIX zlokalizować](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Zobacz także
- [Rozszerzenie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [MenuCommands programu vs. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)
- [Sprzedawać i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)