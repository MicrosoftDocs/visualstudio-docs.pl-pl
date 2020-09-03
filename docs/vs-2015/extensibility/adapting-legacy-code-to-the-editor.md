---
title: Adaptacja starszego kodu do edytora | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184923"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Dostosowanie starszego kodu do edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor programu Visual Studio ma wiele funkcji, do których można uzyskać dostęp z istniejących składników kodu. Poniższe instrukcje pokazują, jak dostosować składnik inny niż MEF, na przykład pakietu VSPackage, aby korzystać z funkcji edytora. Instrukcje pokazują również, jak używać kart sieciowych do uzyskiwania usług edytora w kodzie zarządzanym i niezarządzanym.  
  
## <a name="editor-adapters"></a>Adaptery edytora  
 Adaptery edytora lub podkładki są otokami dla obiektów edytora, które również uwidaczniają klasy i interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop> interfejsie API. Za pomocą kart można przechodzić między usługami spoza edytora, na przykład polecenia powłoki programu Visual Studio i usługi edytora. (W ten sposób Edytor jest obecnie hostowany w programie Visual Studio). Karty umożliwiają również poprawne działanie starszych rozszerzeń edytora i usługi językowej w programie Visual Studio.  
  
## <a name="using-editor-adapters"></a>Korzystanie z adapterów edytora  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Zapewnia metody, które przełączają się między nowym interfejsem edytora i starszymi interfejsami, a także metody tworzące karty.  
  
 W przypadku korzystania z tej usługi w części składnika MEF można zaimportować usługę w następujący sposób.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Jeśli chcesz używać tej usługi w składniku innym niż MEF, postępuj zgodnie z instrukcjami w sekcji "Korzystanie z usług edytora programu Visual Studio w składniku innym niż MEF" w dalszej części tego tematu.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Przełączanie między nowym interfejsem API edytora i starszym interfejsem API  
 Użyj następujących metod, aby przełączać się między obiektem edytora i starszym interfejsem.  
  
|Metoda|Konwersja|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Konwertuje <xref:Microsoft.VisualStudio.Text.ITextBuffer> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Konwertuje <xref:Microsoft.VisualStudio.Text.Editor.ITextView> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|  
  
## <a name="creating-adapters"></a>Tworzenie kart  
 Użyj następujących metod, aby utworzyć karty dla starszych interfejsów.  
  
|Metoda|Konwersja|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> dla określonego elementu <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dla elementu <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Tworzenie kart w kodzie niezarządzanym  
 Wszystkie klasy kart są zarejestrowane do lokalnego współtworzenia i mogą być tworzone przy użyciu `VsLocalCreateInstance()` funkcji.  
  
 Wszystkie karty są tworzone przy użyciu identyfikatorów GUID, które są zdefiniowane w pliku vsshlids. h w... Folder \VisualStudioIntegration\Common\Inc\ instalacji zestawu SDK programu Visual Studio. Aby utworzyć wystąpienie elementu VsTextBufferAdapter, użyj poniższego kodu.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Tworzenie kart w kodzie zarządzanym  
 W kodzie zarządzanym można utworzyć karty w taki sam sposób, jak w przypadku kodu niezarządzanego. Możesz również użyć usługi MEF, która umożliwia tworzenie i pracę z kartami. Dzięki temu można uzyskać dokładniejszą kontrolę, niż w przypadku jej tworzenia.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Aby utworzyć adapter dla IVsTextView  
  
1. Dodaj odwołanie do Microsoft.VisualStudio.Editor.dll. Upewnij się, że `CopyLocal` jest ustawiona na `false` .  
  
2. Utwórz wystąpienie programu w <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> następujący sposób.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Wywołaj `CreateX()` metodę.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Korzystanie z edytora programu Visual Studio bezpośrednio z kodu niezarządzanego  
 Przestrzeń nazw Microsoft. VisualStudio. platform. VSEditor i Microsoft. VisualStudio. platform. VSEditor. Interop współdziałają z wywoływanymi przez COM interfejsami jako IVx * interfejsami. Na przykład interfejs Microsoft. VisualStudio. platform. VSEditor. Interop. IVxTextBuffer jest wersją modelu COM <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfejsu. W programie `IVxTextBuffer` można uzyskać dostęp do migawek buforów, zmodyfikować bufor, nasłuchiwać zdarzeń zmiany tekstu w buforze oraz utworzyć punkty śledzenia i zakresy. Poniższe kroki pokazują, jak uzyskać dostęp do programu `IVxTextBuffer` z programu `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Aby uzyskać IVxTextBuffer  
  
1. Definicje dla interfejsów IVx * znajdują się w pliku VSEditor. h w... Folder \VisualStudioIntegration\Common\Inc\ instalacji zestawu SDK programu Visual Studio.  
  
2. Poniższy kod tworzy wystąpienie buforu tekstowego przy użyciu `IVsUserData->GetData()` metody. W poniższym kodzie `pData` jest wskaźnikiem do `IVsUserData` obiektu.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Korzystanie z usług edytora programu Visual Studio w składniku innym niż MEF  
 Jeśli masz istniejący składnik kodu zarządzanego, który nie korzysta z MEF i chcesz użyć usług edytora programu Visual Studio, musisz dodać odwołanie do zestawu, który zawiera ComponentModelHost pakietu VSPackage i uzyskać swoją usługę SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Aby korzystać ze składników edytora programu Visual Studio ze składnika innego niż MEF  
  
1. Dodaj odwołanie do zestawu Microsoft.VisualStudio.ComponentModelHost.dll w... Folder \Common7\IDE\ instalacji programu Visual Studio. Upewnij się, że `CopyLocal` jest ustawiona na `false` .  
  
2. Dodaj prywatną `IComponentModel` składową do klasy, w której chcesz używać usług edytora programu Visual Studio w następujący sposób.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Utwórz wystąpienie modelu składnika w metodzie inicjacji dla składnika.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Następnie możesz uzyskać dowolną z usług edytora programu Visual Studio, wywołując `IComponentModel.GetService<T>()` metodę dla usługi, którą chcesz.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
