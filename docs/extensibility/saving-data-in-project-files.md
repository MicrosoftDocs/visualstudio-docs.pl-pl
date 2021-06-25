---
title: Zapisywanie danych w plikach projektu | Microsoft Docs
description: Dowiedz się więcej o interfejsach zapewnianych przez platformę Managed Package Framework do zapisywania i pobierania danych specyficznych dla podtypu w pliku projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5859fc9286a3e584c04ccacc1d8b8a35d98dea89
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904984"
---
# <a name="save-data-in-project-files"></a>Zapisywanie danych w plikach projektu
Podtyp projektu może zapisywać i pobierać dane specyficzne dla podtypu w pliku projektu. Program Managed Package Framework (MPF) udostępnia dwa interfejsy do wykonania tego zadania:

- Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> umożliwia dostęp do wartości właściwości z sekcji **MSBuild** pliku projektu. Metody udostępniane przez program mogą być wywoływane przez dowolnego użytkownika za każdym razem, gdy użytkownik musi załadować lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> zapisać dane powiązane z kompilacją.

- Jest <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> używany do utrwalania danych niezwiązywalnych z kompilacją w formacie XML w formacie swobodnym. Metody udostępniane przez program są wywoływane przez usługę za każdym razem, gdy metoda musi utrwalić dane niepowiązywalne z kompilacją <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w pliku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu.

  Aby uzyskać więcej informacji na temat utrwalania danych związanych z kompilacją i niepowiązywalnych z kompilacją, zobacz Utrwalanie danych [w pliku projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Zapisywanie i pobieranie danych związanych z kompilacją

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Aby zapisać dane związane z kompilacją w pliku projektu

- Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodę , aby zapisać pełną ścieżkę pliku projektu.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Aby pobrać dane dotyczące kompilacji z pliku projektu

- Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> metodę , aby pobrać pełną ścieżkę pliku projektu.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>Zapisywanie i pobieranie danych niepowiązynych z kompilacją

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Aby zapisać dane inne niż związane z kompilacją w pliku projektu

1. Zaim implementuj metodę , aby określić, czy fragment XML zmienił się od <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> czasu ostatniego zapisania go w bieżącym pliku.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>Zaim implementuj metodę , aby zapisać dane XML w pliku projektu.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Aby pobrać dane inne niż związane z kompilacją w pliku projektu

1. <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A>Zaim implementuj metodę , aby zainicjować właściwości rozszerzenia projektu i inne dane niezależne od kompilacji. Ta metoda jest wywoływana, jeśli w pliku projektu nie ma żadnych danych konfiguracji XML.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>Zaim implementuj metodę , aby załadować dane XML z pliku projektu.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> Wszystkie przykłady kodu podane w tym temacie są częściami większego przykładu w [przykładach VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Zobacz też
- [Utrwalanie danych w pliku projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
