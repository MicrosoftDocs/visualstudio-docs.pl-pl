---
title: Widoki jedną i wieloma kartami | Dokumentacja firmy Microsoft
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
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8231581761199be4df9c368494fb27bdc7926c51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748995"
---
# <a name="single-and-multi-tab-views"></a>Widoki z jedną i wieloma kartami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor można tworzyć różne typy widoków. Przykładem jest oknem edytora kodu, jest inny Projektant formularzy.  
  
 Widok z wieloma kartami jest widok, który ma wiele kart. Na przykład, edytor HTML obsługuje dwie karty u dołu: **projektowania** i **źródła**, każdy widok logiczny. Widok projektu wyświetla renderowanej strony sieci web, podczas gdy druga Wyświetla zawartość HTML, która obejmuje strony sieci web.  
  
## <a name="accessing-physical-views"></a>Uzyskiwanie dostępu do widoków fizycznych  
 Widoki fizyczne dokumentu widoku obiekty hostów, każdy reprezentuje widok danych w buforze, takie jak kod lub formularz. W związku z tym każdy obiekt widoku dokumentu ma widoku fizycznego (identyfikowanych na podstawie czegoś znanego jako ciąg widoku fizycznego), a pojedynczy widok logiczny.  
  
 Jednak w niektórych przypadkach fizyczny widok może mieć co najmniej dwóch widoków logiczne. Przykłady to edytor który ma podzielonym oknie z widokami side-by-side i Projektant formularzy, widok graficzny interfejs użytkownika/projektu i widok związanego z — — w postaci kodu.  
  
 Aby włączyć tego edytora, aby uzyskać dostęp do wszystkich dostępnych widoków fizycznego, należy utworzyć ciąg widoku fizycznego unikatowy dla każdego typu obiektu widoku dokumentu, który można utworzyć usługi fabryka edytora. Na przykład [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] fabryka edytora dokument można utworzyć widoku obiektów okna kodu i okno projektanta formularzy.  
  
## <a name="creating-multi-tabbed-views"></a>Tworzenie widoków z wieloma kartami  
 Chociaż obiekt widoku dokumentu musi być skojarzony z fizyczny widok przy użyciu ciągu unikatowy widoku fizycznego, można umieścić w wielu kartach w widoku fizycznych, aby umożliwić wyświetlanie danych na różne sposoby. W tej konfiguracji z wieloma kartami wszystkie karty są skojarzone z tego samego ciągu fizyczny widok, ale każda karta jest podany inny widok logiczny identyfikator GUID.  
  
 Aby utworzyć widok z wieloma kartami dla edytora, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> interfejsu, a następnie powiązanie inny widok logiczny identyfikator GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) w każdej karcie można utworzyć.  
  
 Edytor programu Visual Studio HTML jest przykładem edytor z wieloma kartami widoku. Ma ona **projektowania** i **źródła** karty. Aby je włączyć, inny widok logiczny jest skojarzony z każdą kartę `LOGICALVIEWID_TextView` dla **projektowania** kartę i `LOGICALVIEWID_Code` dla **źródła** kartę.  
  
 Określając odpowiedni widok logiczny, pakietu VSPackage mają dostęp do widoku, który odnosi się do określonego celu, na przykład projektowania formularza edycji kodu i debugowania kodu. Jednak okien musi posiadać pusty ciąg, a to musi odpowiadać głównej widok logiczny (`LOGVIEWID_Primary`).  
  
 W poniższej tabeli wymieniono wartości dostępne widok logiczny i ich użycia.  
  
|IDENTYFIKATOR GUID LOGVIEWID|Zalecane użycie|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Widok domyślny/podstawowej fabryki edytora.<br /><br /> Wszystkie fabryki edytora musi obsługiwać tę wartość. Ten widok, musisz użyć pusty ciąg jako jego parametry fizyczny widok. Ta wartość musi być równa co najmniej jeden widok logiczny.|  
|`LOGVIEWID_Debugging`|Debugowanie widoku. Zazwyczaj `LOGVIEWID_Debugging` mapuje do tego samego widoku jako `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Wyświetl uruchomione przez **Wyświetl kod** polecenia.|  
|`LOGVIEWID_Designer`|Wyświetl uruchomione przez **Wyświetl formularz** polecenia.|  
|`LOGVIEWID_TextView`|Widoku edytora tekstu. Jest to widok, który zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, z którego dostęp można uzyskać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Monituje użytkownika o wybranie, które widok do używania.|  
|`LOGVIEWID_ProjectSpecificEditor`|Przekazywany przez **Otwórz za pomocą** okno dialogowe<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Kiedy użytkownik naciśnie pozycję "(domyślny edytor projektu)".|  
  
 Mimo że widok logiczny identyfikatorów GUID to rozszerzalny, można użyć tylko widok logiczny identyfikatory GUID są zdefiniowane w Twojej pakietu VSPackage.  
  
 Podczas zamykania Visual Studio zachowuje identyfikator GUID fabryki edytora i ciągi fizyczny widok skojarzony z oknem dokumentu, dzięki czemu można ponownie otworzyć dokument w systemie windows, po ponownym otwarciu rozwiązania. Tylko systemu windows, które są otwarte, po zamknięciu rozwiązania są utrwalane w pliku rozwiązania (.suo). Te wartości odpowiadają `VSFPROPID_guidEditorType` i `VSFPROPID_pszPhysicalView` wartości przekazane w `propid` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody.  
  
## <a name="example"></a>Przykład  
 Ten fragment kodu ilustruje sposób, w jaki <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> umożliwia dostęp do widoku, który implementuje obiekt `IVsCodeWindow`. W tym przypadku <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> usługi służy do wywoływania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> i żądania `LOGVIEWID_TextView`, która uzyskuje wskaźnik do ramki okna. Wskaźnik do dokumentu obiekt widoku można uzyskać przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> i określając wartość `VSFPROPID_DocView`. Z obiektu widoku dokumentu `QueryInterface` jest wywoływana dla `IVsCodeWindow`. Oczekuje się w tym przypadku, Edytor tekstu jest zwracana, a więc zwracany obiekt widoku dokumentu w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodą jest okna kodu.  
  
```cpp#  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Porady: dołączanie widoków do danych dokumentów](../extensibility/how-to-attach-views-to-document-data.md)   
 [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)

