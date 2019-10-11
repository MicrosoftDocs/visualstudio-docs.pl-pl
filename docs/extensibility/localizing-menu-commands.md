---
title: Lokalizowanie poleceń menu | Microsoft Docs
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b2b42143c2971bcbb172958b8da42a1e887e4699
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252640"
---
# <a name="localize-menu-commands"></a>Lokalizowanie poleceń menu

Można zapewnić zlokalizowany tekst dla poleceń menu i pasków narzędzi, tworząc zlokalizowane pliki *vsct* i zlokalizowane pliki *resx* dla pakietu VSPackage, a następnie aktualizując pliki projektu w celu uwzględnienia zmian.

Informacje o sposobie lokalizowania środowiska instalacji znajdują się w temacie [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalizowanie nazw poleceń

W pakietów VSPackage, polecenia menu i przyciski paska narzędzi są zdefiniowane w pliku *. vsct* .

1. W **Eksplorator rozwiązań**Zmień nazwę pliku *. vsct* z *filename. vsct* na *filename. en-us. vsct*.

2. Utwórz kopię *pliku filename. en-us. vsct* dla każdego zlokalizowanego języka.

    Nazwij każdą nazwę *pliku kopii. { Locale}. vsct*, gdzie *{locale}* jest określoną nazwą kultury. Aby zapoznać się z listą wartości nazw kultur, zobacz [identyfikatory ustawień regionalnych przypisanych przez firmę Microsoft](/windows/uwp/publish/supported-languages).

    *Nazwa pliku. Pliki locale. vsct* będą zawierać zlokalizowany tekst menu pakietu.

3. Otwórz każdą *nazwę pliku. Plik locale. vsct* do lokalizowania tekstu.

   1. Zmodyfikuj wartości elementu [ButtonText](../extensibility/buttontext-element.md) zgodnie z potrzebami dla określonego języka.

   2. Jeśli będziesz udostępniać zlokalizowane ikony, zmodyfikuj wartości [mapy bitowej](../extensibility/bitmap-element.md) , aby wskazywały na pliki docelowe.

      Poniższy przykład przedstawia tekst przycisku w języku angielskim i hiszpańskim, aby otworzyć okno narzędzia Eksploratora drzewa rodziny.

      [*FamilyTree. pl-US. vsct*]

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

    [*FamilyTree.es-ES. vsct*]

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

Zasoby tekstowe inne niż nazwy poleceń są zdefiniowane w plikach zasobów ( *. resx*).

1. Zmień nazwę *pakietu VSPackage. resx* na *pakietu VSPackage. pl-US. resx*.

2. Utwórz kopię pliku *pakietu VSPackage. pl-US. resx* dla każdego zlokalizowanego języka.

     Nazwij wszystkie kopie *pakietu VSPackage. { Locale}. resx*, gdzie *{locale}* jest określoną nazwą kultury.

3. Zmień nazwę pliku *resources. resx* na *resources. pl-US. resx*.

4. Utwórz kopię pliku *resources. en-us. resx* dla każdego zlokalizowanego języka.

     Nazwij wszystkie *zasoby kopiowania. { Locale}. resx*, gdzie *{locale}* jest określoną nazwą kultury.

5. Otwórz każdy plik *resx* , aby zmodyfikować wartości ciągu odpowiednio do określonego języka i kultury. Poniższy przykład pokazuje zlokalizowaną definicję zasobu na pasku tytułu okna narzędzi.

     [*Resources. pl-US. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Uwzględnij zlokalizowane zasoby w projekcie

Należy zmodyfikować plik *AssemblyInfo.cs* i plik projektu, aby uwzględnić zlokalizowane zasoby.

1. W węźle **Właściwości** w **Eksplorator rozwiązań**Otwórz *AssemblyInfo.cs* lub *AssemblyInfo. vb* w edytorze.

2. Dodaj następujący wpis.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Powoduje to ustawienie języka angielskiego na angielski jako język domyślny.

3. Zwolnij projekt.

4. Otwórz plik projektu w edytorze.

5. W elemencie głównym `Project` Dodaj element `PropertyGroup` z elementem `UICulture`, który jest zgodny z językiem domyślnym.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Powoduje to ustawienie angielskiej wersji językowej US jako domyślnej kultury interfejsu użytkownika dla formantów Windows Presentation Foundation (WPF).

6. Znajdź element `ItemGroup`, który zawiera elementy `EmbeddedResource`.

7. W elemencie `EmbeddedResource`, który wywołuje *pakietu VSPackage. pl-US. resx*, Zastąp element `ManifestResourceName` elementem `LogicalName`, który jest ustawiony na `VSPackage.en-US.Resources` w następujący sposób:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Dla każdego zlokalizowanego języka Skopiuj element `EmbeddedResource` dla `VsPackage.en-US`, a następnie ustaw atrybut **include** i **LogicalName** elementu kopii na ustawienia regionalne docelowej.

9. Dla każdego zlokalizowanego elementu `VSCTCompile` Dodaj element `ResourceName`, który wskazuje na `Menus.ctmenu`, jak pokazano w następującym przykładzie:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Zapisz plik projektu i ponownie Załaduj projekt.

11. Skompiluj projekt.

     Spowoduje to utworzenie zestawu głównego i zestawów zasobów dla każdego języka. Aby uzyskać informacje na temat lokalizowania procesu wdrażania, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md) .

## <a name="see-also"></a>Zobacz także
- [Poszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [MenuCommands a OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)
- [Globalizacja i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
