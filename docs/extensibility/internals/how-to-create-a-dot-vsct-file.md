---
title: 'Instrukcje: Utwórz. Plik vsct | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3155ff69db461e652b11ff6e8ec6d405000244f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924181"
---
# <a name="how-to-create-a-vsct-file"></a>Instrukcje: Utwórz plik. vsct

Istnieje kilka sposobów tworzenia pliku konfiguracji tabeli poleceń programu Visual Studio opartego na języku XML ( *. vsct*).

- Nowy pakietu VSPackage można utworzyć w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] szablonie pakietu.

- Do wygenerowania pliku z istniejącego pliku *CTC* można użyć kompilatora konfiguracji tabeli poleceń opartych na języku XML, *vsct. exe*.

- Można użyć *vsct. exe* , aby wygenerować plik *. vsct* z istniejącego pliku *. Dyrektor ds* .

- Nowy plik *. vsct* można utworzyć ręcznie.

  W tym artykule wyjaśniono, jak ręcznie utworzyć nowy plik *. vsct* .

### <a name="to-manually-create-a-new-vsct-file"></a>Aby ręcznie utworzyć nowy plik. vsct

1. Rozpocznij [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **pliku**.

3. W okienku **Szablony** kliknij **plik XML** , a następnie kliknij przycisk **Otwórz**.

4. W menu **Widok** kliknij polecenie **Właściwości** , aby wyświetlić właściwości pliku XML.

5. W oknie **Właściwości** kliknij przycisk **Przeglądaj** we właściwości **schematy** .

6. Na liście schematów XSD wybierz schemat *vsct. xsd* . Jeśli nie ma go na liście, kliknij przycisk **Dodaj** , a następnie Znajdź plik na dysku lokalnym. Po zakończeniu kliknij przycisk **OK** .

7. W pliku XML, wpisz *< polecenie* , a następnie naciśnij klawisz **Tab**. Zamknij tag, wpisując *>* .

    Ta akcja tworzy plik Basic *. vsct* .

8. Wypełnij elementy pliku XML, który chcesz dodać, zgodnie z odwołaniem do [schematu XML vsct](../../extensibility/vsct-xml-schema-reference.md). Aby uzyskać więcej informacji, zobacz [pliki Author. vsct](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Instrukcje: Utwórz plik. vsct z istniejącego pliku CTC

Można utworzyć plik *. vsct* opartego na języku XML z istniejącej tabeli poleceń *. CTC* plik źródłowy. Dzięki temu można skorzystać z nowego formatu kompilatora tabeli poleceń opartych na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] języku XML (vsct).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Aby utworzyć plik. vsct z pliku. CTC

1. Uzyskaj kopię języka Perl.

2. Uzyskaj kopię skryptu Perl *ConvertCTCToVSCT.pl*, zwykle znajdującą się w  *\<ścieżce instalacji zestawu Visual Studio SDK > folder \VisualStudioIntegration\Tools\bin* .

3. Uzyskaj kopię pliku źródłowego *. CTC* , który chcesz skonwertować.

4. Umieść pliki w tym samym katalogu.

5. W oknie wiersza polecenia przejdź do katalogu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

6. Typ

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    gdzie *PkgCmd. CTC* jest nazwą pliku *. CTC* i *PkgCmd. vsct* to nazwa pliku *. vsct* , który ma zostać utworzony.

    Ta akcja powoduje utworzenie nowego pliku źródłowego tabeli poleceń XML. *vsct* . Plik można skompilować za pomocą *vsct. exe*, kompilatora vsct, tak jak każdy inny plik *. vsct* .

   > [!NOTE]
   > Można zwiększyć czytelność pliku *. vsct* przez ponowne SFORMATOWANIE komentarzy XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Instrukcje: Utwórz plik. vsct z istniejącego pliku dyrektor ds

Można utworzyć plik *vsct* oparty na języku XML z istniejącego pliku binarnego *. Dyrektor ds* . Dzięki temu można korzystać z nowego formatu kompilatora tabeli poleceń. Ten proces działa nawet wtedy, gdy plik *. Dyrektor ds* został skompilowany z pliku *CTC* . Plik *. vsct* można edytować i skompilować w innym pliku. Dyrektor ds.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Aby utworzyć plik. vsct z pliku. Dyrektor ds

1. Uzyskaj kopie pliku *. Dyrektor ds* i odpowiadający mu plik *. CTSYM* .

2. Umieść pliki w tym samym katalogu, co kompilator *vsct. exe* .

3. W wierszu polecenia programu Visual Studio przejdź do katalogu, który zawiera pliki *. Dyrektor ds* i *. CTSYM* .

4. Typ

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     gdzie \< \<ctofilename\> \<\> jest nazwą pliku dyrektor ds, vsctfilename jest nazwą pliku. vsct, który ma zostać utworzony, a symfilename to nazwa\> plik *. CTSYM* .

     Ten proces powoduje utworzenie nowego pliku kompilatora tabeli poleceń XML *vsct* . Można edytować i kompilować plik z *vsct. exe*, kompilatorem vsct, tak jak każdy inny plik *. vsct* .

## <a name="compile-the-code"></a>Skompilować kod
 Po prostu dodanie pliku *vsct* do projektu nie powoduje jego skompilowania. Należy wprowadzić je w procesie kompilacji.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Aby dodać plik. vsct do kompilacji projektu

1. Otwórz plik projektu w edytorze. Jeśli projekt jest ładowany, najpierw go Zwolnij.

2. Dodaj [element grupy elementów](../../msbuild/itemgroup-element-msbuild.md) , który zawiera `VSCTCompile` element, jak pokazano w poniższym przykładzie.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Element powinien być zawsze ustawiony na `Menus.ctmenu`. `ResourceName`

3. Jeśli projekt zawiera plik *. resx* , Dodaj `EmbeddedResource` `MergeWithCTO` element, który zawiera element, jak pokazano w następującym przykładzie:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Ten znacznik powinien być umieszczony wewnątrz `ItemGroup` elementu, który zawiera osadzone zasoby.

4. Otwórz plik pakietu, zazwyczaj o nazwie  *\<ProjectName\>Package.cs* lub  *\<ProjectName\>Package. vb*, w edytorze.

5. `ProvideMenuResource` Dodaj atrybut do klasy pakietu, jak pokazano w poniższym przykładzie.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Pierwsza wartość parametru musi być zgodna z wartością `ResourceName` atrybutu, który został zdefiniowany w pliku projektu.

## <a name="see-also"></a>Zobacz także
- [Author. vsct — pliki](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Dokumentacja schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)