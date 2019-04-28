---
title: 'Instrukcje: Tworzenie. Pliku Vsct | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c671467f220e61de5ca9de56a2515a2e4836020
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418468"
---
# <a name="how-to-create-a-vsct-file"></a>Instrukcje: Tworzenie pliku vsct

Istnieje kilka sposobów, aby utworzyć konfigurację tabeli polecenia opartych na języku XML programu Visual Studio (*vsct*) pliku.

- Można utworzyć nowego pakietu VSPackage w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pakietu szablonu.

- Można użyć kompilatora konfiguracji tabeli polecenia opartego na języku XML, *Vsct.exe*, aby wygenerować plik z istniejącego *.ctc* pliku.

- Możesz użyć *Vsct.exe* do generowania *vsct* plików z istniejącej *.cto* pliku.

- Można ręcznie utworzyć nowy *vsct* pliku.

  W tym artykule wyjaśniono, jak ręcznie utworzyć nową *vsct* pliku.

### <a name="to-manually-create-a-new-vsct-file"></a>Aby ręcznie utworzyć nowego pliku vsct

1. Rozpocznij [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **pliku**.

3. W **szablony** okienku kliknij **pliku XML** a następnie kliknij przycisk **Otwórz**.

4. Na **widoku** menu, kliknij przycisk **właściwości** Aby wyświetlić jej właściwości w pliku XML.

5. W **właściwości** okna, kliknij przycisk **Przeglądaj** znajdujący się na **schematów** właściwości.

6. Na liście schematy XSD, wybierz *vsct.xsd* schematu. Jeśli nie jest na liście, kliknij przycisk **Dodaj** a następnie znajdź plik na dysku lokalnym. Kliknij przycisk **OK** po zakończeniu.

7. W pliku XML, wpisz *< CommandTable* , a następnie naciśnij klawisz **kartę**. Tag zamykający, wpisując *>*.

    Ta akcja powoduje utworzenie prostej *vsct* pliku.

8. Wypełnij elementów pliku XML, który chcesz dodać, zgodnie z [odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md). Aby uzyskać więcej informacji, zobacz [tworzenie plików vsct](../../extensibility/internals/authoring-dot-vsct-files.md)

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Instrukcje: Tworzenie pliku vsct z istniejącego pliku .ctc

Można tworzyć oparte na języku XML *vsct* plików z istniejącej tabeli polecenia *.ctc* pliku źródłowego. Dzięki temu możesz korzystać z zalet nowego opartego na języku XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] format kompilatora tabeli (VSCT) polecenia.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Do utworzenia pliku vsct z pliku .ctc

1. Uzyskaj kopię programu języka Perl.

2. Uzyskaj kopię skryptu Perl *ConvertCTCToVSCT.pl*, która zwykle znajduje się w  *\<ścieżka instalacji programu Visual Studio SDK > \VisualStudioIntegration\Tools\bin* folderu.

3. Uzyskaj kopię programu *.ctc* pliku źródłowego, który ma zostać przekonwertowany.

4. Umieść pliki w tym samym katalogu.

5. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia monitu okna, przejdź do katalogu.

6. Typ

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    gdzie *PkgCmd.ctc* nazywa się *.ctc* pliku i *PkgCmd.vsct* nazywa się *vsct* pliku, który chcesz utworzyć.

    Ta akcja powoduje utworzenie nowego *vsct* plik źródłowy tabeli poleceń XML. Plik można skompilować przy użyciu *Vsct.exe*, kompilatora VSCT, jak będą inne *vsct* pliku.

   > [!NOTE]
   > Można zwiększyć czytelność *vsct* pliku przez ponowne formatowanie komentarze XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Instrukcje: Tworzenie pliku vsct z istniejącego pliku .cto

Można tworzyć oparte na języku XML *vsct* plik z istniejących danych binarnych *.cto* pliku. W ten sposób pozwala na korzystanie z zalet nowego formatu kompilatora tabeli poleceń. Ten proces działa nawet wtedy, gdy *.cto* plik został skompilowany z *.ctc* pliku. Możesz edytować i skompilować *vsct* pliku do innego pliku .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Do utworzenia pliku vsct z pliku .cto

1. Uzyskaj kopię *.cto* plików i odpowiadającymi mu dostawcami *.ctsym* pliku.

2. Umieść pliki w tym samym katalogu co *vsct.exe* kompilatora.

3. W wierszu polecenia programu Visual Studio, przejdź do katalogu, który zawiera *.cto* i *.ctsym* plików.

4. Typ

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     gdzie \<ctofilename\> nazywa się *.cto* pliku \<vsctfilename\> nazywa się *vsct* pliku, dla którego chcesz utworzyć, a \<symfilename\> nazywa się *.ctsym* pliku.

     Ten proces tworzy nowy *vsct* pliku kompilatora tabeli poleceń XML. Możesz edytować i skompiluj plik za pomocą *vsct.exe*, kompilatora vsct, jak będą inne *vsct* pliku.

## <a name="compile-the-code"></a>Skompilować kod
 Wystarczy dodać *vsct* plik do projektu nie spowoduje jej do kompilowania. Musi ona zawierać w procesie kompilacji.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Aby dodać pliku vsct do kompilacji projektu

1. Otwórz plik projektu w edytorze. Jeśli projekt jest ładowany, należy go najpierw zwolnienia.

2. Dodaj [itemgroup — element](../../msbuild/itemgroup-element-msbuild.md) zawierający `VSCTCompile` elementu, jak pokazano w poniższym przykładzie.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     `ResourceName` Element powinien być zawsze ustawiony na `Menus.ctmenu`.

3. Jeśli projekt zawiera *resx* Dodaj `EmbeddedResource` element, który zawiera `MergeWithCTO` elementu, jak pokazano w poniższym przykładzie:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Ten kod znaczników powinien przeprowadzić wewnątrz `ItemGroup` zawierający zasoby osadzone.

4. Otwórz plik pakietu, zwykle o nazwie  *\<ProjectName\>Package.cs* lub  *\<ProjectName\>Package.vb*, w edytorze.

5. Dodaj `ProvideMenuResource` atrybutów do klasy pakietu, jak pokazano w poniższym przykładzie.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Pierwsza wartość parametru musi być zgodna wartość `ResourceName` atrybut zdefiniowany w pliku projektu.

## <a name="see-also"></a>Zobacz także
- [Tworzenie plików vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Pliki tabeli (vsct) polecenia programu Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)