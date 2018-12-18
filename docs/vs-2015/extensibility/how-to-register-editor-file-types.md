---
title: 'Porady: Rejestrowanie typów plików edytora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 39b1cde8dec71df9cb85bf737c23c883fbdcd615
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777269"
---
# <a name="how-to-register-editor-file-types"></a>Porady: rejestrowanie Edytor typów plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najprostszym sposobem zarejestrowania Edytor typów plików jest za pomocą atrybutów rejestracji w ramach [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] zarządzanych klas framework (MPF) pakietu. W przypadku wdrażania pakietu w trybie macierzystym [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], można także napisać skrypt rejestru, który rejestruje edytora i rozszerzenia skojarzone.  
  
## <a name="registration-using-mpf-classes"></a>Rejestracja przy użyciu klas MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Aby zarejestrować Edytor typów plików, przy użyciu klas MPF  
  
1.  Podaj <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> klasy za pomocą odpowiednich parametrów dla Twojego edytora w klasie usługi pakietu VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Gdzie ". Przykład"to rozszerzenie, które jest zarejestrowany dla tego edytora, a"32"jest jego poziom priorytetu.  
  
     `projectGuid` To identyfikator GUID pliku różne typy, zdefiniowane w <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Typ pliku inny zostanie podany, dzięki czemu wynikowy plik nie będzie to część procesu kompilacji.  
  
     `TemplateDir` reprezentuje folder, który zawiera pliki szablonów, które są dołączone do przykładu zarządzanych Edytor języka basic.  
  
     `NameResourceID` jest zdefiniowana w pliku Resources.h BasicEditorUI projektu i identyfikuje edytora edytorem"Moje".  
  
2.  Zastąp <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
     W danej implementacji <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody, wywołanie <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> metody i przekazać wystąpienia fabryki edytora, jak pokazano poniżej.  
  
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
  
     W tym kroku rejestruje fabryki edytora i rozszerzenia plików edytora.  
  
3.  Wyrejestruj fabryki edytora.  
  
     Po usunięciu pakietu VSPackage, fabryki edytora są automatycznie wyrejestrowana. Jeśli obiekt fabryki edytora implementuje <xref:System.IDisposable> interfejsu, jego `Dispose` metoda jest wywoływana po fabryka ma został wyrejestrowany z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Rejestracja za pomocą skryptów rejestru  
 Zarejestrowanie fabryki edytora i typów plików w macierzystym [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] odbywa się przy użyciu skryptu rejestru do zapisu do rejestru systemu windows, zgodnie z przedstawionymi poniżej.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Aby zarejestrować Edytor typów plików za pomocą skryptów rejestru  
  
1.  W skrypcie rejestru, zdefiniuj fabryki edytora i fabryka Edytora ciągu identyfikatora GUID pokazany na `GUID_BscEditorFactory` sekcji poniższy skrypt rejestru. Ponadto można zdefiniować rozszerzenie i priorytet rozszerzenie edytora:  
  
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
  
     Rozszerzenie pliku edytora, w tym przykładzie jest identyfikowany jako "RTF" i "50" jest jej priorytet. Identyfikator GUID ciągi są zdefiniowane w pliku Resource.h BscEdit przykładowego projektu.  
  
2.  Rejestrowanie pakietu VSPackage.  
  
3.  Zarejestrować fabryki edytora.  
  
     Fabryka edytora jest zarejestrowany w <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementacji.  
  
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
  
     Identyfikator GUID ciągi są zdefiniowane w pliku Resource.h BscEdit projektu.

