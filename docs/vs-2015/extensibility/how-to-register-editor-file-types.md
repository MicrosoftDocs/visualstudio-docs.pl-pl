---
title: 'Instrukcje: rejestrowanie typów plików edytora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204118"
---
# <a name="how-to-register-editor-file-types"></a>Instrukcje: rejestrowanie typów plików edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najprostszym sposobem rejestrowania typów plików edytora jest użycie atrybutów rejestracji dostarczonych jako część [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] klas MPF (Managed Package Framework). Jeśli pakiet jest wdrażany w trybie macierzystym [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , można również napisać skrypt rejestru, który rejestruje Edytor i skojarzone rozszerzenia.  
  
## <a name="registration-using-mpf-classes"></a>Rejestracja przy użyciu klas MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Aby zarejestrować typy plików edytora przy użyciu klas MPF  
  
1. Podaj <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> klasę z odpowiednimi parametrami dla edytora w klasie pakietu VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Gdzie ". Przykładem jest rozszerzenie, które jest zarejestrowane dla tego edytora, a "32" jest jego poziom priorytetu.  
  
     `projectGuid`Jest to identyfikator GUID dla różnych typów plików, zdefiniowany w <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . Typ pliku różnego jest dostarczany, dzięki czemu otrzymany plik nie będzie częścią procesu kompilacji.  
  
     `TemplateDir` reprezentuje folder zawierający pliki szablonów, które są zawarte w przykładowym zarządzanym edytorze Basic.  
  
     `NameResourceID` jest zdefiniowany w pliku Resources. h projektu BasicEditorUI i identyfikuje Edytor jako "mój Edytor".  
  
2. Zastąp <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodę.  
  
     W implementacji <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody należy wywołać <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> metodę i przekazać wystąpienie fabryki edytora, jak pokazano poniżej.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Ten krok rejestruje zarówno fabrykę edytora, jak i rozszerzenia plików edytora.  
  
3. Wyrejestruj fabryky edytora.  
  
     Fabryki edytora są automatycznie wyrejestrowani po usunięciu pakietu VSPackage. Jeśli obiekt fabryki edytora implementuje <xref:System.IDisposable> interfejs, jego `Dispose` Metoda jest wywoływana po wyrejestrowaniu fabryki w usłudze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Rejestracja przy użyciu skryptu rejestru  
 Rejestrowanie fabryk edytora i typów plików w trybie macierzystym odbywa [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] się przy użyciu skryptu rejestru do zapisu w rejestrze systemu Windows, jak pokazano poniżej.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Aby zarejestrować typy plików edytora przy użyciu skryptu rejestru  
  
1. W skrypcie rejestru Zdefiniuj fabrykę edytora i ciąg identyfikatora GUID fabryki edytora, jak pokazano w `GUID_BscEditorFactory` sekcji następującego skryptu rejestru. Ponadto Zdefiniuj rozszerzenie i priorytet rozszerzenia edytora:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     Rozszerzenie pliku edytora w tym przykładzie jest identyfikowane jako ". rtf", a jego priorytet to "50". Ciągi identyfikatorów GUID są zdefiniowane w pliku Resource. h projektu przykładowego BscEdit.  
  
2. Zarejestruj pakietu VSPackage.  
  
3. Zarejestruj fabrykę edytora.  
  
     Fabryka edytora jest zarejestrowana w <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementacji.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     Ciągi identyfikatorów GUID są zdefiniowane w pliku Resource. h projektu BscEdit.
