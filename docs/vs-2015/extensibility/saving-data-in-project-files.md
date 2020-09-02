---
title: Zapisywanie danych w plikach projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc671963854e4fa0c2af763de5000fac82a839b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817563"
---
# <a name="saving-data-in-project-files"></a>Zapisywanie danych w plikach projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podtyp projektu może zapisać i pobrać dane specyficzne dla określonego typu w pliku projektu. Struktura pakietu zarządzanego (MPF) udostępnia dwa interfejsy do wykonania tego zadania:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>Interfejs umożliwia dostęp do wartości właściwości z sekcji programu **MSBuild** w pliku projektu. Metody dostarczone przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> mogą być wywoływane przez dowolnego użytkownika za każdym razem, gdy użytkownik musi załadować lub zapisać dane związane z kompilacją.  
  
- Służy <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> do utrwalania danych niezwiązanych z niekompilacją w postaci pliku XML o dowolnej postaci. Metody dostarczone przez <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> są wywoływane przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zawsze, gdy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] muszą utrzymywać dane niezwiązane z niekompilacją w pliku projektu.  
  
  Aby uzyskać więcej informacji na temat utrwalania danych kompilacji i niezwiązanych z kompilacją, zobacz [utrwalanie danych w pliku projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="saving-and-retrieving-build-related-data"></a>Zapisywanie i pobieranie danych związanych z kompilacją  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>Aby zapisać dane dotyczące kompilacji w pliku projektu  
  
- Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodę, aby zapisać pełną ścieżkę do pliku projektu.  
  
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
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Aby pobrać dane dotyczące kompilacji z pliku projektu  
  
- Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> metodę, aby pobrać pełną ścieżkę do pliku projektu.  
  
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
  
## <a name="saving-and-retrieving-non-build-related-data"></a>Zapisywanie i pobieranie danych niezwiązanych z kompilacją  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>Aby zapisać dane niezwiązane z niekompilacją w pliku projektu  
  
1. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> metodę, aby określić, czy fragment kodu XML został zmieniony od czasu ostatniego zapisania go w bieżącym pliku.  
  
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
  
2. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metodę, aby zapisać dane XML w pliku projektu.  
  
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
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Aby pobrać dane niezwiązane z kompilacją w pliku projektu  
  
1. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> metodę, aby zainicjować właściwości rozszerzenia projektu i innych danych niezależnych od kompilacji. Ta metoda jest wywoływana, jeśli w pliku projektu nie ma danych konfiguracji XML.  
  
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
  
2. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> metodę w celu załadowania danych XML z pliku projektu.  
  
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
> Wszystkie przykłady kodu podane w tym temacie są częścią większego przykładu [VSSDK Samples](../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Utrwalanie danych w pliku projektu programu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
