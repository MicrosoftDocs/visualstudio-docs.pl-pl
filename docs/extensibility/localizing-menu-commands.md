---
title: Lokalizowanie poleceń menu | Microsoft Docs
description: Dowiedz się, jak zapewnić zlokalizowany tekst dla poleceń menu i pasków narzędzi, tworząc zlokalizowane pliki vsct i zlokalizowane pliki RESX dla pakietu VSPackage.
ms.custom: SEO-VS-2020
ms.date: 10/08/2019
ms.topic: how-to
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
ms.openlocfilehash: 51f3692a4539eddbf35e24de8024eadd39031080
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615606"
---
# <a name="localize-menu-commands"></a>Lokalizowanie poleceń menu

Można zapewnić zlokalizowany tekst dla poleceń menu i pasków narzędzi, tworząc zlokalizowane pliki *vsct* i zlokalizowane pliki *resx* dla pakietu VSPackage, a następnie aktualizując pliki projektu w celu uwzględnienia zmian.

Informacje o sposobie lokalizowania środowiska instalacji znajdują się w temacie [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalizowanie nazw poleceń

W pakietów VSPackage, polecenia menu i przyciski paska narzędzi są zdefiniowane w pliku *. vsct* .

1. W **Eksplorator rozwiązań** Zmień nazwę pliku *. vsct* z *filename. vsct* na *filename. en-us. vsct*.

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

Zasoby tekstowe inne niż nazwy poleceń są zdefiniowane w plikach zasobów (*. resx*).

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

1. W węźle **Właściwości** w **Eksplorator rozwiązań** Otwórz *AssemblyInfo.cs* lub *AssemblyInfo. vb* w edytorze.

2. Dodaj następujący wpis.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Powoduje to ustawienie języka angielskiego na angielski jako język domyślny.

3. Zwolnij projekt.

4. Otwórz plik projektu w edytorze.

5. W elemencie głównym `Project` Dodaj `PropertyGroup` element z `UICulture` elementem, który jest zgodny z językiem domyślnym.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Powoduje to ustawienie angielskiej wersji językowej US jako domyślnej kultury interfejsu użytkownika dla formantów Windows Presentation Foundation (WPF).

6. Znajdź `ItemGroup` element, który zawiera `EmbeddedResource` elementy.

7. W `EmbeddedResource` elemencie, który wywołuje *pakietu VSPackage. en-us. resx*, Zastąp `ManifestResourceName` element elementem `LogicalName` , który jest ustawiony na `VSPackage.en-US.Resources` , w następujący sposób:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Dla każdego zlokalizowanego języka Skopiuj  `EmbeddedResource` element dla `VsPackage.en-US` i ustaw atrybut **include** i **LogicalName** elementu kopii na wartość ustawienia regionalne docelowej.

9. Do każdego zlokalizowanego `VSCTCompile` elementu Dodaj element wskazujący `ResourceName` `Menus.ctmenu` , jak pokazano w następującym przykładzie:

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
- [Globalizacja i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
