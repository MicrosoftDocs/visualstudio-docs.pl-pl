---
title: Rozszerzanie filtru Eksploratora rozwiązań | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef9439d9cebfa8b80b214e52d077ab1f770d4750
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912129"
---
# <a name="extend-the-solution-explorer-filter"></a>Rozszerzanie filtru Eksploratora rozwiązań
Możesz rozszerzyć **Eksploratora rozwiązań** filtrowania funkcji, aby pokazać lub ukryć poszczególne pliki. Na przykład można utworzyć filtr, który zawiera tylko pliki C# klasy fabryki w **Eksploratora rozwiązań**, tak jak pokazano w tym przewodniku.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Tworzenie projektu pakietu Visual Studio

1. Utwórz projekt VSIX, o nazwie `FileFilter`. Dodawanie polecenia niestandardowego szablonu elementu o nazwie **obiektu FileFilter**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dodaj odwołanie do `System.ComponentModel.Composition` i `Microsoft.VisualStudio.Utilities`.

3. Polecenie menu są wyświetlane na **Eksploratora rozwiązań** paska narzędzi. Otwórz *FileFilterPackage.vsct* pliku.

4. Zmiana `<Button>` bloku do następującego:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Aktualizacja pliku manifestu

1. W *source.extension.vsixmanifest* plików, Dodaj element zawartości, która jest składnik MEF.

2. Na **zasoby** kartę, wybrać **New** przycisku.

3. W **typu** wybierz opcję **Microsoft.VisualStudio.MefComponent**.

4. W **źródła** wybierz opcję **projekt w bieżącym rozwiązaniu**.

5. W **projektu** wybierz opcję **obiektu FileFilter**, a następnie wybierz **OK** przycisku.

### <a name="add-the-filter-code"></a>Dodaj kod filtru

1. Dodaj niektóre identyfikatorów GUID *FileFilterPackageGuids.cs* pliku:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Dodaj plik klasy do obiektu FileFilter projektu o nazwie *FileNameFilter.cs*.

3. Zamień pustej przestrzeni nazw i pusta klasa poniższy kod.

     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Metoda przyjmuje kolekcji, która zawiera katalog główny rozwiązania (`rootItems`) i zwraca kolekcję elementów, które mają zostać uwzględnione w filtrze.

     `ShouldIncludeInFilter` Metoda filtruje elementy w **Eksploratora rozwiązań** hierarchii odpowiednio, pod warunkiem, że można określić.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. W *FileFilter.cs*, Usuń położenie polecenia i obsługę kodu z konstruktora obiektu FileFilter. Wynik powinien wyglądać następująco:

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     Usuń `ShowMessageBox()` również metody.

5. W *FileFilterPackage.cs*, Zastąp kod w `Initialize()` metoda następującym kodem:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Testowanie kodu

1. Skompiluj i uruchom projekt. Zostanie wyświetlone drugie wystąpienie programu Visual Studio. Jest to wystąpienie eksperymentalne.

2. W doświadczalnym wystąpieniu programu Visual Studio Otwórz projekt C#.

3. Poszukaj przycisku można dodać na **Eksploratora rozwiązań** paska narzędzi. Powinna to być czwarty przycisk z lewej strony.

4. Kliknij przycisk, powinny być odfiltrowane wszystkie pliki i powinien zostać wyświetlony **wszystkie elementy zostały wyfiltrowane z widoku.** w **Eksploratora rozwiązań**.