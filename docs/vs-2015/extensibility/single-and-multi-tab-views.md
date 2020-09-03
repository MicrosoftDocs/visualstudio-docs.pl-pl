---
title: Pojedyncze i wielotabulacjowe widoki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 804a37a43ffe25335dc522542f5035b0882e63ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205563"
---
# <a name="single-and-multi-tab-views"></a>Widoki z jedną i wieloma kartami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor może tworzyć różne typy widoków. Przykładem jest okno edytora kodu, inne jest projektantem formularzy.  
  
 Widok z wieloma kartami to widok, który ma wiele kart. Na przykład edytor HTML ma dwie karty w dolnej części: **projekt** i **Źródło**, każdy widok logiczny. Widok projektu wyświetla wyrenderowaną stronę sieci Web, podczas gdy druga wyświetla HTML, który składa się ze strony sieci Web.  
  
## <a name="accessing-physical-views"></a>Dostęp do widoków fizycznych  
 Widoki fizyczne obiekty widoku dokumentu, z których każdy reprezentuje widok danych w buforze, taki jak kod lub formularz. W związku z tym każdy obiekt widoku dokumentu ma widok fizyczny (identyfikowany przez coś znanego jako ciąg widoku fizycznego) i ogólnie pojedynczy widok logiczny.  
  
 W niektórych przypadkach widok fizyczny może mieć co najmniej dwa widoki logiczne. Niektóre przykłady to edytor, który ma okno podziału z widokami Side-by-Side lub projektantem formularzy, który ma graficzny interfejs użytkownika/projekt i widok związany z kodem.  
  
 Aby umożliwić edytorowi dostęp do wszystkich dostępnych widoków fizycznych, należy utworzyć unikatowy ciąg widoku fizycznego dla każdego typu obiektu widoku dokumentu, który może zostać utworzony przez fabrykę edytora. Na przykład [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] fabryka edytora może tworzyć obiekty widoku dokumentu dla okna kodu i okna Projektanta formularzy.  
  
## <a name="creating-multi-tabbed-views"></a>Tworzenie widoków z obsługą wiele kart  
 Chociaż obiekt widoku dokumentu musi być skojarzony z widokiem fizycznym za pomocą unikatowego ciągu widoku fizycznego, można umieścić wiele kart w widoku fizycznym, aby umożliwić wyświetlanie danych na różne sposoby. W tej konfiguracji z wielodostępnymi kartami wszystkie karty są skojarzone z tym samym ciągiem widoku fizycznego, ale każda karta ma inny identyfikator GUID widoku logicznego.  
  
 Aby utworzyć widok z wielodostępnym edytorem, zaimplementuj interfejs, <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> a następnie skojarz inny identyfikator GUID widoku logicznego ( <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> ) z każdą utworzoną kartą.  
  
 Edytor HTML programu Visual Studio jest przykładem edytora z wielodostępnym widokiem. Zawiera karty **projektowe** i **źródłowe** . Aby włączyć tę opcję, inny widok logiczny jest skojarzony z każdą kartą, `LOGICALVIEWID_TextView` na karcie **projekt** i `LOGICALVIEWID_Code` na karcie **Źródło** .  
  
 Określając odpowiedni widok logiczny, pakietu VSPackage może uzyskać dostęp do widoku, który odnosi się do określonego celu, na przykład projektowania formularza, edytowania kodu lub debugowania kodu. Jednak jedno z okien musi być identyfikowane przez ciąg o wartości NULL i musi odpowiadać podstawowemu widokowi logicznemu ( `LOGVIEWID_Primary` ).  
  
 W poniższej tabeli wymieniono dostępne wartości widoku logicznego i ich użycie.  
  
|IDENTYFIKATOR GUID LOGVIEWID|Zalecane użycie|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Domyślny/podstawowy widok fabryki edytora.<br /><br /> Wszystkie fabryki edytora muszą obsługiwać tę wartość. Ten widok musi używać PUSTEgo ciągu jako jego fizycznego ciągu widoku. Co najmniej jeden widok logiczny musi być ustawiony na tę wartość.|  
|`LOGVIEWID_Debugging`|Widok debugowania. Zazwyczaj program `LOGVIEWID_Debugging` mapuje do tego samego widoku co `LOGVIEWID_Code` .|  
|`LOGVIEWID_Code`|Widok uruchamiany przez polecenie **Wyświetl kod** .|  
|`LOGVIEWID_Designer`|Widok uruchamiany przez polecenie **Widok formularza** .|  
|`LOGVIEWID_TextView`|Widok edytora tekstu. Jest to widok, który zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> , z którego można uzyskać dostęp <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
|`LOGVIEWID_UserChooseView`|Poprosi użytkownika o wybranie widoku, który ma być używany.|  
|`LOGVIEWID_ProjectSpecificEditor`|Zakończone przez okno dialogowe **Otwórz za pomocą** , aby<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> gdy użytkownik wybierze wpis "(edytor domyślny projektu)".|  
  
 Mimo że identyfikatory GUID widoku logicznego są rozszerzalne, można używać tylko identyfikatorów GUID widoku logicznego zdefiniowanych w pakietu VSPackage.  
  
 Po zamknięciu program Visual Studio zachowuje identyfikator GUID fabryki edytora oraz ciągi widoku fizycznego skojarzone z oknem dokumentu, aby można było go użyć do ponownego otwarcia okna dokumentu po ponownym otwarciu rozwiązania. W pliku rozwiązania (. suo) są utrwalane tylko okna otwarte, gdy rozwiązanie zostało zamknięte. Te wartości odpowiadają `VSFPROPID_guidEditorType` i `VSFPROPID_pszPhysicalView` wartościom przesłanym w `propid` parametrze w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodzie.  
  
## <a name="example"></a>Przykład  
 W tym fragmencie kodu pokazano, jak <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> obiekt jest używany w celu uzyskania dostępu do widoku, który implementuje `IVsCodeWindow` . W takim przypadku <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> Usługa jest używana do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> i żądania `LOGVIEWID_TextView` , które uzyskuje wskaźnik do ramki okna. Wskaźnik do obiektu widoku dokumentu jest uzyskiwany przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> i określenie wartości `VSFPROPID_DocView` . Z obiektu widoku dokumentu `QueryInterface` jest wywoływana dla `IVsCodeWindow` . Oczekuje się, że w tym przypadku jest zwracany Edytor tekstu, a więc obiekt widoku dokumentu zwrócony w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodzie jest oknem kodu.  
  
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
 [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md)   
 [Instrukcje: dołączanie widoków do danych dokumentu](../extensibility/how-to-attach-views-to-document-data.md)   
 [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)
