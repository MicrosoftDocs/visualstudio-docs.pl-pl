---
title: Widoki jedno- i wielokadłowe | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699988"
---
# <a name="single-and-multi-tab-views"></a>Widoki z jedną i wieloma kartami
Edytor może tworzyć różne typy widoków. Jednym z przykładów jest okno edytora kodu, innym jest projektant formularzy.

 Widok z wieloma kartami to widok, który ma wiele kart. Na przykład edytor HTML ma dwie karty u dołu: **Design** i **Source**, każdy widok logiczny. W widoku projektu wyświetlana jest wyrenderowana strona internetowa, a druga — kod HTML zawierający stronę internetową.

## <a name="accessing-physical-views"></a>Uzyskiwanie dostępu do widoków fizycznych
 Widoki fizyczne hostują obiekty widoku dokumentu, z których każdy reprezentuje widok danych w buforze, takich jak kod lub formularz. W związku z tym każdy obiekt widoku dokumentu ma widok fizyczny (identyfikowany przez coś znanego jako ciąg widoku fizycznego) i ogólnie pojedynczy widok logiczny.

 W niektórych przypadkach widok fizyczny może mieć dwa lub więcej widoków logicznych. Niektóre przykłady to edytor, który ma podzielone okno z widokami obok siebie lub projektant formularzy, który ma widok GUI/design i widok kodu za formularzem.

 Aby umożliwić edytorowi dostęp do wszystkich dostępnych widoków fizycznych, należy utworzyć unikatowy ciąg widoku fizycznego dla każdego typu obiektu widoku dokumentu, który może utworzyć fabryka edytora. Na przykład [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] fabryka edytora może tworzyć obiekty widoku dokumentu dla okna kodu i okna projektanta formularzy.

## <a name="creating-multi-tabbed-views"></a>Tworzenie widoków z wieloma kartami
 Chociaż obiekt widoku dokumentu musi być skojarzony z widokiem fizycznym za pomocą unikatowego ciągu widoku fizycznego, można umieścić wiele kart w widoku fizycznym, aby umożliwić wyświetlanie danych na różne sposoby. W tej konfiguracji z wieloma kartami wszystkie karty są skojarzone z tym samym ciągiem widoku fizycznego, ale każda karta ma inny identyfikator GUID widoku logicznego.

 Aby utworzyć widok z wieloma kartami dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> edytora, zaimplementuj<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>interfejs, a następnie skojarzyć inny identyfikator GUID widoku logicznego ( ) z każdą utworzoną kartą.

 Edytor HTML programu Visual Studio jest przykładem edytora z widokiem wielokadłkowym. Posiada karty **Projektowanie** i **Źródło.** Aby to włączyć, z każdą kartą, `LOGICALVIEWID_TextView` kartę **Projektowanie** i `LOGICALVIEWID_Code` kartę **Źródło,** jest skojarzony inny widok logiczny.

 Określając odpowiedni widok logiczny, VSPackage może uzyskać dostęp do widoku, który odpowiada określonego celu, takiego jak projektowanie formularza, edytowanie kodu lub debugowania kodu. Jednak jedno z okien musi być identyfikowane przez ciąg NULL i`LOGVIEWID_Primary`musi to odpowiadać podstawowemu widokowi logicznemu ( ).

 W poniższej tabeli wymieniono dostępne wartości widoku logicznego i ich użycie.

|IDENTYFIKATOR LOGVIEWID|Zalecane zastosowanie|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Domyślny/podstawowy widok fabryki edytora.<br /><br /> Wszystkie fabryki edytora muszą obsługiwać tę wartość. Ten widok musi używać ciągu NULL jako ciągu widoku fizycznego. Co najmniej jeden widok logiczny musi być ustawiony na tę wartość.|
|`LOGVIEWID_Debugging`|Debugowania widoku. Zazwyczaj `LOGVIEWID_Debugging` mapy do tego samego `LOGVIEWID_Code`widoku co .|
|`LOGVIEWID_Code`|Widok uruchamiany przez polecenie **Wyświetl kod.**|
|`LOGVIEWID_Designer`|Widok uruchomiony przez polecenie **Wyświetl formularz.**|
|`LOGVIEWID_TextView`|Widok edytora tekstu. Jest to widok, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>który zwraca , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>z którego można uzyskać dostęp .|
|`LOGVIEWID_UserChooseView`|Monituje użytkownika, aby wybrać widok do użycia.|
|`LOGVIEWID_ProjectSpecificEditor`|Przekazywane przez okno dialogowe **Otwieranie za pomocą**<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> gdy użytkownik wybierze wpis "(Domyślny edytor projektu)".|

 Chociaż identyfikatory GUID widoku logicznego są rozszerzalne, można używać tylko identyfikatorów GUID widoku logicznego zdefiniowanych w programie VSPackage.

 Po zamknięciu programu Visual Studio zachowuje identyfikator GUID fabryki edytora i ciągi widoku fizycznego skojarzone z oknem dokumentu, dzięki czemu może służyć do ponownego otwierania okien dokumentów po ponownym otwarciu rozwiązania. Tylko okna, które są otwarte, gdy rozwiązanie jest zamknięte są utrwalone w pliku rozwiązania (.suo). Wartości te odpowiadają `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` wartościom i `propid` wartościom <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> przekazanym w parametrze w metodzie.

## <a name="example"></a>Przykład
 Ten fragment kodu ilustruje <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> sposób, w jaki obiekt `IVsCodeWindow`jest używany do uzyskiwania dostępu do widoku implementuujące . W takim przypadku <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> usługa jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> używana `LOGVIEWID_TextView`do wywoływania i żądania , który uzyskuje wskaźnik do ramki okna. Wskaźnik do obiektu widoku dokumentu uzyskuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> się przez wywołanie i określenie wartości `VSFPROPID_DocView`. Z obiektu widoku `QueryInterface` dokumentu jest `IVsCodeWindow`wywoływana dla . Oczekiwanie w tym przypadku jest, że edytor tekstu jest zwracany, a więc obiekt widoku dokumentu zwrócony w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodzie jest okno kodu.

```cpp
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
- [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)
- [Instrukcje: dołączanie widoków do danych dokumentów](../extensibility/how-to-attach-views-to-document-data.md)
- [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)
