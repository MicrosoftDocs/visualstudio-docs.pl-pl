---
title: 'Instrukcje: Tworzenie. Plik vsct | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158350"
---
# <a name="how-to-create-a-vsct-file"></a>Instrukcje: tworzenie pliku Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Istnieje kilka sposobów tworzenia pliku konfiguracji tabeli poleceń programu Visual Studio opartego na języku XML (. vsct).  
  
- Nowy pakietu VSPackage można utworzyć w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] szablonie pakietu.  
  
- Do wygenerowania pliku z istniejącego pliku. CTC można użyć kompilatora konfiguracji tabeli poleceń opartych na języku XML Vsct.exe.  
  
- Za pomocą Vsct.exe można wygenerować plik. vsct z istniejącego pliku. Dyrektor ds.  
  
- Nowy plik. vsct można utworzyć ręcznie.  
  
  W tym temacie wyjaśniono, jak ręcznie utworzyć nowy plik. vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Aby ręcznie utworzyć nowy plik. vsct  
  
1. Rozpocznij [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **plik**.  
  
3. W okienku **Szablony** kliknij **plik XML** , a następnie kliknij przycisk **Otwórz**.  
  
4. W menu **Widok** kliknij **okno właściwości** , aby wyświetlić właściwości pliku XML.  
  
5. W oknie **Właściwości** kliknij przycisk Przeglądaj (...) we właściwości schematy.  
  
6. Na liście schematów XSD wybierz schemat vsct. xsd. Jeśli nie ma go na liście, kliknij przycisk **Dodaj** , a następnie Znajdź plik na dysku lokalnym. Po zakończeniu kliknij przycisk **OK** .  
  
7. W pliku XML wpisz, `<CommandTable` a następnie naciśnij klawisz Tab. Zamknij tag, wpisując `>` .  
  
     Spowoduje to utworzenie podstawowego pliku. vsct.  
  
8. Wypełnij elementy pliku XML, który chcesz dodać, zgodnie ze [schematem vsct](../../extensibility/vsct-xml-schema-reference.md). Aby uzyskać więcej informacji, zobacz [Tworzenie. Pliki vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Po prostu dodanie pliku vsct do projektu nie powoduje jego skompilowania. Należy wprowadzić je w procesie kompilacji.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Aby dodać plik. vsct do kompilacji projektu  
  
1. Otwórz plik projektu w edytorze. Jeśli projekt jest ładowany, najpierw go Zwolnij.  
  
2. Dodaj [element grupy elementów](../../msbuild/itemgroup-element-msbuild.md) , który zawiera element VSCTCompile, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Element resourceName powinien zawsze być ustawiony na `Menus.ctmenu` .  
  
3. Jeśli projekt zawiera plik. resx, Dodaj element EmbeddedResource, który zawiera element MergeWithCTO, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Ten znacznik powinien nastąpić wewnątrz elementu Item, który zawiera osadzone zasoby.  
  
4. Otwórz plik pakietu, zazwyczaj o nazwie *ProjectName*Package.cs lub *ProjectName*Package. vb, w edytorze.  
  
5. Dodaj atrybut ProvideMenuResource do klasy Package, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Pierwsza wartość parametru musi być zgodna z wartością atrybutu resourceName zdefiniowanego w pliku projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Projekt. Pliki vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabela poleceń programu Visual Studio (. Vsct) — pliki](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Instrukcje: Tworzenie. Plik vsct z istniejącego. Plik CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Instrukcje: Tworzenie. Plik vsct z istniejącego. Plik dyrektor ds](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
