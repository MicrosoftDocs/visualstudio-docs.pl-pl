---
title: 'Porady: tworzenie. Pliku Vsct | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bbfdcf605a1c4346874ec222937a458225788151
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802639"
---
# <a name="how-to-create-a-vsct-file"></a>Porady: tworzenie. Pliku Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Istnieje kilka sposobów, aby utworzyć plik konfiguracji (vsct) oparte na języku XML programu Visual Studio polecenie tabeli.  
  
- Można utworzyć nowego pakietu VSPackage w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pakietu szablonu.  
  
- Kompilator konfiguracji tabeli polecenia opartego na języku XML, Vsct.exe, można użyć, aby wygenerować plik z istniejącego pliku .ctc.  
  
- Vsct.exe służy do generowania pliku vsct z istniejącego pliku .cto.  
  
- Można ręcznie utworzyć nowego pliku vsct.  
  
  W tym temacie wyjaśniono, jak ręcznie utworzyć nowego pliku vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Aby ręcznie utworzyć nowego pliku vsct  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **pliku**.  
  
3.  W **szablony** okienku kliknij **pliku XML** a następnie kliknij przycisk **Otwórz**.  
  
4.  Na **widoku** menu, kliknij przycisk **okno właściwości** Aby wyświetlić jej właściwości w pliku XML.  
  
5.  W **właściwości** okna, kliknij przycisk przeglądania (...) we właściwości schematów.  
  
6.  Na liście schematy XSD wybierz schemat vsct.xsd. Jeśli nie jest na liście, kliknij przycisk **Dodaj** a następnie znajdź plik na dysku lokalnym. Kliknij przycisk **OK** po zakończeniu.  
  
7.  W pliku XML, wpisz `<CommandTable` a następnie naciśnij klawisz TAB. Tag zamykający, wpisując `>`.  
  
     Spowoduje to utworzenie pliku vsct podstawowe.  
  
8.  Wypełnij elementów pliku XML, który chcesz dodać, zgodnie z [schematu VSCT](../../extensibility/vsct-xml-schema-reference.md). Aby uzyskać więcej informacji, zobacz [tworzenie. Pliki Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Dodanie pliku vsct do projektu nie spowoduje jej do kompilowania. Musi ona zawierać w procesie kompilacji.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Aby dodać pliku vsct do kompilacji projektu  
  
1.  Otwórz plik projektu w edytorze. Jeśli projekt jest ładowany, należy go najpierw zwolnienia.  
  
2.  Dodaj [itemgroup — element](../../msbuild/itemgroup-element-msbuild.md) zawierający VSCTCompile element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName element powinna zawsze być ustawiona na `Menus.ctmenu`.  
  
3.  Jeśli projekt zawiera plik Resx, Dodaj element EmbeddedResource, który zawiera MergeWithCTO element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Ten kod znaczników powinny przejść w elemencie ItemGroup, który zawiera zasoby osadzone.  
  
4.  Otwórz plik pakietu, zwykle o nazwie *ProjectName*Package.cs lub *ProjectName*Package.vb w edytorze.  
  
5.  Dodaj atrybut ProvideMenuResource do klasy pakietu, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Pierwsza wartość parametru musi być zgodna wartość atrybutu ResourceName, które zostały zdefiniowane w pliku projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie. Pliki Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabeli poleceń programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Porady: tworzenie. Plik Vsct z istniejącej. Plik CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Porady: tworzenie. Plik Vsct z istniejącej. Plik Dyrektor ds. technologii](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

