---
title: 'Instrukcje: Rejestrowanie typów plików edytora | Dokumentacja firmy Microsoft'
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23a3277a550b17371b4d8315da64eb7507c8c863
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857805"
---
# <a name="how-to-register-editor-file-types"></a>Instrukcje: Zarejestruj Edytor typów plików
Najprostszym sposobem zarejestrowania Edytor typów plików jest za pomocą atrybutów rejestracji w ramach [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] zarządzanych klas framework (MPF) pakietu. W przypadku wdrażania pakietu w trybie macierzystym [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], można także napisać skrypt rejestru, który rejestruje edytora i rozszerzenia skojarzone.

## <a name="registration-using-mpf-classes"></a>Rejestracja przy użyciu klas MPF

### <a name="to-register-editor-file-types-using-mpf-classes"></a>Aby zarejestrować Edytor typów plików, przy użyciu klas MPF

1. Podaj <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> klasy za pomocą odpowiednich parametrów dla Twojego edytora w klasie usługi pakietu VSPackage.

   ```
   [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,
        ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",
        TemplateDir = "..\\..\\Templates",
        NameResourceID = 106)]
   ```

    Gdzie *. Przykładowe* to rozszerzenie, które jest zarejestrowany dla tego edytora, a "32" jest jej priorytet.

    `projectGuid` To identyfikator GUID pliku różne typy, zdefiniowane w <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Typ pliku inny zostanie podany, dzięki czemu wynikowy plik nie będzie to część procesu kompilacji.

    *TemplateDir* reprezentuje folder, który zawiera pliki szablonów, które są dołączone do przykładu zarządzanych Edytor języka basic.

    `NameResourceID` jest zdefiniowany w *Resources.h* pliku projektu BasicEditorUI i identyfikuje edytora edytorem"Moje".

2. Zastąp <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.

    W danej implementacji <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody, wywołanie <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> metody i przekazać wystąpienia fabryki edytora, jak pokazano poniżej.

   ```csharp
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

3. Wyrejestruj fabryki edytora.

    Po usunięciu pakietu VSPackage, fabryki edytora są automatycznie wyrejestrowana. Jeśli obiekt fabryki edytora implementuje <xref:System.IDisposable> interfejsu, jego `Dispose` metoda jest wywoływana po fabryka ma został wyrejestrowany z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="registration-using-a-registry-script"></a>Rejestracja za pomocą skryptów rejestru
 Zarejestrowanie fabryki edytora i typów plików w macierzystym [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] odbywa się przy użyciu skryptu rejestru do zapisu do rejestru systemu windows, zgodnie z przedstawionymi poniżej.

### <a name="to-register-editor-file-types-using-a-registry-script"></a>Aby zarejestrować Edytor typów plików za pomocą skryptów rejestru

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

     Rozszerzenie pliku edytora, w tym przykładzie jest identyfikowany jako *.rtf* i jego priorytet jest "50". Identyfikator GUID ciągi są zdefiniowane w *Resource.h* pliku BscEdit przykładowy projekt.

2.  Rejestrowanie pakietu VSPackage.

3.  Zarejestrować fabryki edytora.

     Fabryka edytora jest zarejestrowany w <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementacji.

    ```cpp
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

     Identyfikator GUID ciągi są zdefiniowane w *Resource.h* pliku projektu BscEdit.