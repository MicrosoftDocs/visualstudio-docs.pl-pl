---
title: Rozszerzanie filtru Eksploratora rozwiązań | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711572"
---
# <a name="extend-the-solution-explorer-filter"></a>Rozszerzanie filtru Eksploratora rozwiązań
Można rozszerzyć funkcje filtrowania **Eksploratora rozwiązań,** aby wyświetlić lub ukryć różne pliki. Na przykład można utworzyć filtr, który pokazuje tylko pliki fabryczne klasy C# w **Eksploratorze rozwiązań,** jak pokazano w tym instruktażu.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Tworzenie projektu pakietu programu Visual Studio

1. Utwórz projekt VSIX o nazwie `FileFilter`. Dodaj niestandardowy szablon elementu polecenia o nazwie **FileFilter**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dodaj odwołanie `System.ComponentModel.Composition` do `Microsoft.VisualStudio.Utilities`i .

3. Aby polecenie menu było wyświetlane na pasku narzędzi **Eksploratora rozwiązań.** Otwórz plik *FileFilterPackage.vsct.*

4. Zmień `<Button>` blok na następujący:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Aktualizowanie pliku manifestu

1. W pliku *source.extension.vsixmanifest* dodaj zasób, który jest składnikiem MEF.

2. Na karcie **Zasoby** wybierz przycisk **Nowy.**

3. W polu **Typ** wybierz pozycję **Microsoft.VisualStudio.MefComponent**.

4. W polu **Źródło** wybierz pozycję **Projekt w bieżącym rozwiązaniu**.

5. W polu **Projekt** wybierz polecenie **FileFilter**, a następnie wybierz przycisk **OK.**

### <a name="add-the-filter-code"></a>Dodawanie kodu filtru

1. Dodaj kilka identyfikatorów GUID do pliku *FileFilterPackageGuids.cs:*

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Dodaj plik klasy do projektu FileFilter o nazwie *FileNameFilter.cs*.

3. Zastąp pusty obszar nazw i pustą klasę poniższym kodem.

     Metoda `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` pobiera kolekcję, która zawiera katalog`rootItems`główny rozwiązania ( ) i zwraca kolekcję elementów, które mają być uwzględnione w filtrze.

     Metoda `ShouldIncludeInFilter` filtruje elementy w hierarchii **Eksploratora rozwiązań** na podstawie określonego warunku.

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

4. W *FileFilter.cs*usuń umieszczenie polecenia i kod obsługi z konstruktora FileFilter. Wynik powinien wyglądać następująco:

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

     Usuń `ShowMessageBox()` również metodę.

5. W *FileFilterPackage.cs*, zastąp `Initialize()` kod w metodzie następującymi:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>testowanie kodu

1. Tworzenie i uruchamianie projektu. Pojawi się drugie wystąpienie programu Visual Studio. Jest to nazywane eksperymentalne wystąpienie.

2. W eksperymentalnym wystąpieniu programu Visual Studio otwórz projekt języka C#.

3. Poszukaj przycisku dodanego na pasku **narzędzi Eksploratora rozwiązań.** Powinien to być czwarty przycisk od lewej.

4. Po kliknięciu przycisku wszystkie pliki powinny zostać odfiltrowane i powinny zostać **wyświetlone Wszystkie elementy zostały odfiltrowane z widoku.** w **Eksploratorze rozwiązań**.
