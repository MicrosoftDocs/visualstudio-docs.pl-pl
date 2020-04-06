---
title: 'Jak: Utwórz plik . Plik vsct | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5a5f53ec87c9447af232e9d0528108ddbaea01a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708105"
---
# <a name="how-to-create-a-vsct-file"></a>Jak: Tworzenie pliku vsct

Istnieje kilka sposobów tworzenia pliku tabeli poleceń programu Visual Studio opartej na języku XML (*vsct*).

- Można utworzyć nowy VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w szablonie pakietu.

- Do wygenerowania pliku z istniejącego pliku *ctc* można użyć kompilatora konfiguracji tabeli poleceń opartych na języku XML, *Vsct.exe.*

- *Program Vsct.exe* umożliwia wygenerowanie pliku *vsct* z istniejącego pliku *cto.*

- Można ręcznie utworzyć nowy plik *vsct.*

  W tym artykule wyjaśniono, jak ręcznie utworzyć nowy plik *vsct.*

### <a name="to-manually-create-a-new-vsct-file"></a>Aby ręcznie utworzyć nowy plik vsct

1. Start [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Plik**.

3. W okienku **Szablony** kliknij pozycję **Plik XML,** a następnie kliknij pozycję **Otwórz**.

4. W menu **Widok** kliknij polecenie **Właściwości,** aby wyświetlić właściwości pliku XML.

5. W oknie **Właściwości** kliknij przycisk **Przeglądaj** we właściwości **Schemas.**

6. Na liście schematów XSD wybierz schemat *vsct.xsd.* Jeśli nie ma go na liście, kliknij przycisk **Dodaj,** a następnie znajdź plik na dysku lokalnym. Po zakończeniu kliknij **przycisk OK.**

7. W pliku XML wpisz *<CommandTable,* a następnie naciśnij **klawisz Tab**. Zamknij znacznik, wpisując *>* plik .

    Ta akcja tworzy podstawowy plik *vsct.*

8. Wypełnij elementy pliku XML, który chcesz dodać, zgodnie z [odwołaniem do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md). Aby uzyskać więcej informacji, zobacz [Author .vsct files](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Jak: Tworzenie pliku vsct z istniejącego pliku ctc

Plik *vsct* oparty na formacie XML można utworzyć z istniejącego pliku źródłowego tabeli poleceń *.ctc.* W ten sposób można skorzystać z nowego formatu kompilatora tabeli poleceń opartych na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] języku XML (VSCT).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Aby utworzyć plik vsct z pliku ctc

1. Uzyskaj kopię języka Perla.

2. Uzyskaj kopię *ConvertCTCToVSCT.pl*skryptu Perla , zwykle znajdującego * \<się w ścieżce instalacji zestawu SDK programu Visual Studio>\VisualStudioIntegration\Tools\bin* folderu.

3. Uzyskaj kopię pliku źródłowego *ctc,* który chcesz przekonwertować.

4. Umieść pliki w tym samym katalogu.

5. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oknie wiersza polecenia przejdź do katalogu.

6. Typ

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    gdzie *PkgCmd.ctc* jest nazwą pliku *.ctc,* a *PkgCmd.vsct* jest nazwą pliku *vsct,* który chcesz utworzyć.

    Ta akcja tworzy nowy plik źródłowy tabeli poleceń *.vsct* XML. Plik można skompilować przy użyciu *vsct.exe*, kompilatora VSCT, tak jak każdy inny plik *vsct.*

   > [!NOTE]
   > Można poprawić czytelność pliku *vsct,* formatując komentarze XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Jak: Tworzenie pliku vsct z istniejącego pliku cto

Plik *vsct* oparty na formacie XML można utworzyć z istniejącego pliku binarnego *.cto.* W ten sposób można skorzystać z nowego formatu kompilatora tabeli poleceń. Ten proces działa nawet wtedy, gdy plik *.cto* został skompilowany z pliku *ctc.* Plik *.vsct* można edytować i kompilować w inny plik .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Aby utworzyć plik vsct z pliku .cto

1. Uzyskaj kopie pliku *.cto* i odpowiadającego mu pliku *.ctsym.*

2. Umieść pliki w tym samym katalogu co kompilator *vsct.exe.*

3. W wierszu polecenia programu Visual Studio przejdź do katalogu zawierającego pliki *.cto* i *.ctsym.*

4. Typ

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     gdzie \<\> ctofilename jest nazwą pliku *.cto,* \<vsctfilename\> to nazwa pliku *vsct,* który \<chcesz utworzyć,\> a symfilename jest nazwą pliku *.ctsym.*

     Ten proces tworzy nowy plik kompilatora tabeli poleceń *.vsct* XML. Można edytować i kompilować plik z *vsct.exe*, kompilator vsct, jak każdy inny plik *vsct.*

## <a name="compile-the-code"></a>Skompiluj kod
 Po prostu dodanie pliku *vsct* do projektu nie powoduje jego skompilowania. Należy włączyć go w procesie kompilacji.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Aby dodać plik vsct do kompilacji projektu

1. Otwórz plik projektu w edytorze. Jeśli projekt jest załadowany, należy go najpierw zwolnić.

2. Dodaj [itemgroup element,](../../msbuild/itemgroup-element-msbuild.md) `VSCTCompile` który zawiera element, jak pokazano w poniższym przykładzie.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Element `ResourceName` powinien być zawsze `Menus.ctmenu`ustawiony na .

3. Jeśli projekt zawiera plik *resx,* `EmbeddedResource` dodaj element `MergeWithCTO` zawierający element, jak pokazano w poniższym przykładzie:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Ten znacznik powinien przejść `ItemGroup` wewnątrz elementu, który zawiera zasoby osadzone.

4. Otwórz plik pakietu o nazwie * \<ProjectName\>Package.cs* lub * \<\>ProjectName Package.vb*w edytorze.

5. Dodaj `ProvideMenuResource` atrybut do klasy pakietu, jak pokazano w poniższym przykładzie.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Pierwsza wartość parametru musi być `ResourceName` zgodna z wartością atrybutu zdefiniowanego w pliku projektu.

## <a name="see-also"></a>Zobacz też
- [Autor plików vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
