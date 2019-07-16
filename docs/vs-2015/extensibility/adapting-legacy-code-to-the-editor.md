---
title: Dostosowanie kodem Legacy do edytora | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184923"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Dostosowanie starszego kodu do edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor programu Visual Studio zawiera wiele funkcji, które można wywołać z istniejącymi elementami kodu. Poniższe instrukcje przedstawiają sposób dostosowania jako składnik MEF nie, na przykład pakietu VSPackage, korzystanie z funkcji edytora. Instrukcje pokazują również jak używać kart usług edytora kodu zarówno zarządzanego i niezarządzanego.  
  
## <a name="editor-adapters"></a>Edytor kart  
 Edytor karty lub podkładki, są otoki dla obiektów edytora, które również udostępnić klasy i interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop> interfejsu API. Można użyć karty, na przykład przenieść między usługami bez edytora, polecenia powłoki programu Visual Studio i usługi edytora. (To jest jak edytor obecnie jest obsługiwany w programie Visual Studio). Karty również włączyć starsze rozszerzenia usługi Edytor i język do prawidłowego działania w programie Visual Studio.  
  
## <a name="using-editor-adapters"></a>Użycie kart edytora  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> Udostępnia metody, które przełączać się między nowe interfejsy edytora i interfejsy starszej wersji, a także metody tworzące kart.  
  
 Korzystania z tej usługi w elemencie MEF składnik usługi można importować w następujący sposób.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Jeśli chcesz korzystać z tej usługi w składniku bez MEF, postępuj zgodnie z instrukcjami w sekcji "Przy użyciu programu Visual Studio Edytor usług w Non-składnik MEF" w dalszej części tego tematu.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Przełączanie między nowego interfejsu API w edytorze i starszej wersji interfejsu API  
 Aby przełączać się między obiekt edytora i starszego interfejsu, należy użyć następujących metod.  
  
|Metoda|Konwersja|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Konwertuje <xref:Microsoft.VisualStudio.Text.ITextBuffer> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Konwertuje <xref:Microsoft.VisualStudio.Text.Editor.ITextView> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Tworzenie kart  
 Użyj poniższych metod, aby utworzyć kart dla starszych interfejsów.  
  
|Metoda|Konwersja|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do określonego <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dla <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Tworzenie kart w niezarządzanym kodzie  
 Wszystkie klasy karty są rejestrowane jako lokalne wspólnie tworzyć i mogą być utworzone przy użyciu `VsLocalCreateInstance()` funkcji.  
  
 Wszystkie karty są tworzone za pomocą identyfikatorów GUID, które są zdefiniowane w pliku vsshlids.h w... \VisualStudioIntegration\Common\Inc\ folderu instalacji zestawu SDK programu Visual Studio. Aby utworzyć wystąpienie VsTextBufferAdapter, użyj następującego kodu.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Tworzenie kart w kodzie zarządzanym  
 W kodzie zarządzanym można wspólnie utworzyć karty sieciowe w taki sam sposób jak te opisane dla niezarządzanego kodu. Można również użyć usługi MEF, która umożliwia tworzenie i wchodzić w interakcje z kartami. Ten sposób pobierania adapter umożliwia bardziej precyzyjną kontrolę niż po utworzeniu wspólnie.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Można utworzyć adaptera dla IVsTextView  
  
1. Dodaj odwołanie do Microsoft.VisualStudio.Editor.dll. Upewnij się, że `CopyLocal` ustawiono `false`.  
  
2. Utwórz wystąpienie <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, wykonując następujące czynności.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Wywołaj `CreateX()` metody.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Za pomocą edytora programu Visual Studio bezpośrednio z kodem niezarządzanym  
 Przestrzeń nazw Microsoft.VisualStudio.Platform.VSEditor i przestrzeni nazw Microsoft.VisualStudio.Platform.VSEditor.Interop uwidocznić interfejsów COM wywoływane, jako IVx * interfejsów. Na przykład interfejs Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer jest wersja COM <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfejsu. Z `IVxTextBuffer`, możesz uzyskać dostęp do migawek buforu, modyfikują bufor, nasłuchiwać zdarzeń zmiany tekstu w buforze i utwórz punkty śledzenia i zakresy. Poniższe kroki pokazują, jak uzyskać dostęp do `IVxTextBuffer` z `IVsTextBuffer`.  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Aby uzyskać IVxTextBuffer  
  
1. Definicje dla interfejsów IVx * znajdują się w pliku VSEditor.h w... \VisualStudioIntegration\Common\Inc\ folderu instalacji zestawu SDK programu Visual Studio.  
  
2. Poniższy kod tworzy buforu tekstowego przy użyciu `IVsUserData->GetData()` metody. W poniższym kodzie `pData` jest wskaźnikiem do `IVsUserData` obiektu.  
  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Za pomocą usług edytora programu Visual Studio w składniku bez MEF  
 Jeśli masz istniejący składnik kodu zarządzanego, który nie korzysta z MEF i chcesz korzystać z usług w edytorze programu Visual Studio, należy dodać odwołanie do zestawu, który zawiera ComponentModelHost VSPackage i pobrać jego SComponentModel usługi.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Korzystających ze składników edytora programu Visual Studio ze składnika bez MEF  
  
1. Dodaj odwołanie do zestawu Microsoft.VisualStudio.ComponentModelHost.dll w... \Common7\IDE\ folder instalacji programu Visual Studio. Upewnij się, że `CopyLocal` ustawiono `false`.  
  
2. Dodaj prywatnej `IComponentModel` składowej klasy, w której chcesz używać usług edytora programu Visual Studio, w następujący sposób.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Tworzy model składników w metodzie inicjalizacji składnika.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Po tym dowolne spośród usług edytora programu Visual Studio można uzyskać przez wywołanie metody `IComponentModel.GetService<T>()` metodę odpowiednią usługę.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
