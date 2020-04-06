---
title: Lokalizowanie poleceń menu | Dokumenty firmy Microsoft
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702944"
---
# <a name="localize-menu-commands"></a>Lokalizowanie poleceń menu

Można podać zlokalizowany tekst dla poleceń menu i paska narzędzi, tworząc zlokalizowane pliki *vsct* i zlokalizowane pliki *.resx* dla programu VSPackage, a następnie aktualizując pliki projektu w celu uwzględnienia zmian.

Aby uzyskać informacje dotyczące lokalizowania instalacji, zobacz [Lokalizuj pakiety VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalizuj nazwy poleceń

W programie VSPackages polecenia menu i przyciski paska narzędzi są definiowane w pliku *vsct.*

1. W **Eksploratorze rozwiązań**zmień nazwę pliku *.vsct* z *filename.vsct* na *filename.en-US.vsct*.

2. Zrób kopię *filename.en-US.vsct* dla każdego zlokalizowanego języka.

    Nazwij każdą *nazwę pliku kopii.{ Locale}.vsct*, gdzie *{Locale}* jest nazwą określonej kultury. Aby uzyskać listę wartości nazw kultury, zobacz [Identyfikatory ustawień regionalnych przypisane przez firmę Microsoft](/windows/uwp/publish/supported-languages).

    Te *nazwy pliku. Pliki Locale.vsct* będą zawierać zlokalizowany tekst menu dla pakietu.

3. Otwórz każdą *nazwę pliku. Plik Locale.vsct* do lokalizowania tekstu.

   1. Zmodyfikuj [buttontext](../extensibility/buttontext-element.md) wartości elementu, zgodnie z potrzebami dla określonego języka.

   2. Jeśli zostaną podane zlokalizowane ikony, zmodyfikuj wartości [bitmapy,](../extensibility/bitmap-element.md) aby wskazywały pliki docelowe.

      W poniższym przykładzie pokazano tekst przycisku w języku angielskim i hiszpańskim dla polecenia otwierania okna narzędzia Drzewa rodzinnego.

      [*FamilyTree.en-US.vsct*]

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

    [*FamilyTree.es-ES.vsct*]

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

## <a name="localize-other-text-resources"></a>Lokalizowanie innych zasobów tekstowych

Zasoby tekstowe inne niż nazwy poleceń są definiowane w plikach zasobu *(.resx).*

1. Zmień nazwę *pliku VSPackage.resx* na *VSPackage.pl-US.resx*.

2. Zrób kopię pliku *VSPackage.en-US.resx* dla każdego zlokalizowanego języka.

     Nazwij każdą kopię *VSPackage.{ Locale}.resx*, gdzie *{Locale}* jest nazwą określonej kultury.

3. Zmień nazwę *pliku Resources.resx* na *Resources.en-US.resx*.

4. Należy wykonać kopię pliku *Resources.en-US.resx* dla każdego zlokalizowanego języka.

     Nazwij każdą kopię *zasobów.{ Locale}.resx*, gdzie *{Locale}* jest nazwą określonej kultury.

5. Otwórz każdy plik *.resx,* aby zmodyfikować wartości ciągu odpowiednie dla określonego języka i kultury. W poniższym przykładzie przedstawiono zlokalizowaną definicję zasobu dla paska tytułu okna narzędzia.

     [*Resources.pl-US.resx*]

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

## <a name="incorporate-localized-resources-into-the-project"></a>Włączenie zlokalizowanych zasobów do projektu

Należy zmodyfikować plik *assemblyinfo.cs* i plik projektu, aby uwzględnić zlokalizowane zasoby.

1. Z węzła **Właściwości** w **Eksploratorze rozwiązań**otwórz *assemblyinfo.cs* lub *assemblyinfo.vb* w edytorze.

2. Dodaj następujący wpis.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Spowoduje to ustawienie języka angielskiego w usa jako języka domyślnego.

3. Zwalnianie projektu.

4. Otwórz plik projektu w edytorze.

5. W elemencie `Project` `PropertyGroup` głównym dodaj `UICulture` element z elementem, który pasuje do domyślnego języka.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Spowoduje to ustawienie języka angielskiego w stanach AMERYKAŃSKIch jako domyślnej kultury interfejsu użytkownika dla formantów Programu Windows Presentation Foundation (WPF).

6. `ItemGroup` Zlokalizuj `EmbeddedResource` element, który zawiera elementy.

7. W `EmbeddedResource` elemencie, który wywołuje *vsPackage.en-US.resx*, zastąp `ManifestResourceName` element elementem, `LogicalName` który jest ustawiony na `VSPackage.en-US.Resources`, w następujący sposób:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Dla każdego zlokalizowanego języka `EmbeddedResource` skopiuj element dla `VsPackage.en-US`, i ustaw atrybut **Include** i element **LogicalName** kopii do ustawień regionalnych obiektu docelowego.

9. Do każdego `VSCTCompile` zlokalizowanego elementu `ResourceName` dodaj element, który wskazuje na `Menus.ctmenu`, jak pokazano w poniższym przykładzie:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Zapisz plik projektu i załaduj ponownie projekt.

11. Skompiluj projekt.

     Spowoduje to utworzenie zestawu głównego i zestawów zasobów dla każdego języka. Aby uzyskać informacje na temat lokalizowania procesu wdrażania, zobacz [Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Globalizacja i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
