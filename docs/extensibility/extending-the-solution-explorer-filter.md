---
title: Rozszerzanie filtru Eksplorator rozwiązań | Microsoft Docs
description: Dowiedz się, jak rozłożyć funkcję filtrowania Eksplorator rozwiązań, aby pokazać lub ukryć różne pliki w zestawie SDK programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dfe2947d60ad5dde6e2f23b9bed59b09e6abe8ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862125"
---
# <a name="extend-the-solution-explorer-filter"></a>Rozwiń filtr Eksplorator rozwiązań
Można rozłożyć funkcję filtrowania **Eksplorator rozwiązań** , aby pokazać lub ukryć różne pliki. Na przykład można utworzyć filtr, który pokazuje tylko pliki fabryki klas języka C# w **Eksplorator rozwiązań**, jak pokazano w tym instruktażu.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Tworzenie projektu pakietu programu Visual Studio

1. Utwórz projekt VSIX o nazwie `FileFilter` . Dodaj niestandardowy szablon elementu polecenia o nazwie **FileFilter**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dodaj odwołanie do `System.ComponentModel.Composition` i `Microsoft.VisualStudio.Utilities` .

3. Utwórz polecenie menu na pasku narzędzi **Eksplorator rozwiązań** . Otwórz plik *FileFilterPackage. vsct* .

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

1. W pliku *source. Extension. vsixmanifest* Dodaj element zawartości, który jest składnikiem MEF.

2. Na karcie **zasoby** wybierz przycisk **Nowy** .

3. W polu **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

4. W polu **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

5. W polu **projekt** wybierz polecenie **FileFilter**, a następnie wybierz przycisk **OK** .

### <a name="add-the-filter-code"></a>Dodaj kod filtru

1. Dodaj niektóre identyfikatory GUID do pliku *FileFilterPackageGuids.cs* :

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Dodaj plik klasy do projektu FileFilter o nazwie *FileNameFilter.cs*.

3. Zastąp pustą przestrzeń nazw i pustą klasę poniższym kodem.

     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`Metoda przyjmuje kolekcję, która zawiera element główny rozwiązania ( `rootItems` ) i zwraca kolekcję elementów do uwzględnienia w filtrze.

     `ShouldIncludeInFilter`Metoda filtruje elementy w hierarchii **Eksplorator rozwiązań** na podstawie określonego warunku.

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

4. W *FileFilter.cs*, Usuń umieszczanie poleceń i kod obsługi z konstruktora FileFilter. Wynik powinien wyglądać następująco:

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

5. W *FileFilterPackage.cs* Zastąp kod w `Initialize()` metodzie następującymi:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Testowanie kodu

1. Skompiluj i Uruchom projekt. Zostanie wyświetlone drugie wystąpienie programu Visual Studio. Nazywa się to eksperymentalnym wystąpieniem.

2. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz projekt C#.

3. Poszukaj przycisku dodanego na pasku narzędzi **Eksplorator rozwiązań** . Powinien to być czwarty przycisk z lewej strony.

4. Po kliknięciu przycisku wszystkie pliki powinny być odfiltrowane i powinny być widoczne **wszystkie elementy, które zostały odfiltrowane z widoku.** w **Eksplorator rozwiązań**.
