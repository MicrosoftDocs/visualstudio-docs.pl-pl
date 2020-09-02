---
title: 'Instrukcje: pomijanie powiadomień o zmianie plików | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204079"
---
# <a name="how-to-suppress-file-change-notifications"></a>Instrukcje: pomijanie powiadomienia o zmianie pliku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy plik fizyczny reprezentujący bufor tekstowy został zmieniony, zostanie wyświetlone okno dialogowe z komunikatem **czy chcesz zapisać zmiany w następujących elementach?** Jest to nazywane powiadomieniem o zmianie pliku. Jeśli jednak wiele zmian będzie się znajdować w pliku, to okno dialogowe, w którym jest wyświetlany zbyt dużo, może szybko stać się irytujące.  
  
 Można programowo pominąć to okno dialogowe, wykonując poniższą procedurę. Dzięki temu można ponownie załadować plik natychmiast bez monitowania użytkownika o zapisanie zmian za każdym razem.  
  
### <a name="to-suppress-file-change-notification"></a>Aby pominąć powiadomienie o zmianie pliku  
  
1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodę, aby określić, który obiekt bufora tekstowego jest skojarzony z otwartym plikiem.  
  
2. Kierowanie <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu znajdującego się w pamięci, aby zignorować zmiany plików monitorowania przez uzyskanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interfejsu z <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu (dane dokumentu), a następnie zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metody z `fIgnore` parametrem ustawionym na `true` .  
  
3. Wywołaj metody z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> i interfejsy, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Aby zaktualizować obiekt w pamięci <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> przy użyciu zmian pliku (na przykład gdy pole zostanie dodane do składnika).  
  
4. Zaktualizuj plik na dysku ze zmianami bez uwzględniania oczekujących edycji, które użytkownik może być w toku.  
  
     W ten sposób, gdy nastąpi przekierowanie <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu w celu wznowienia monitorowania powiadomień o zmianach plików, bufor tekstu w pamięci odzwierciedla zmiany, które zostały wygenerowane, a także wszystkie inne oczekujące zmiany. Plik na dysku odzwierciedla najnowszy kod wygenerowany przez użytkownika i wszystkie wcześniej zapisane zmiany wprowadzane przez użytkowników w kodzie edytowanym przez użytkownika.  
  
5. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodę, aby powiadomić <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiekt, aby wznowić monitorowanie powiadomień o zmianach plików przez ustawienie `fIgnore` parametru na `false` .  
  
6. Jeśli planujesz wprowadzić kilka zmian w pliku, jak w przypadku kontroli kodu źródłowego (SCC), należy poinformować usługę globalnej zmiany pliku, aby tymczasowo wstrzymać powiadomienia o zmianach plików.  
  
     Na przykład, jeśli ponownie napiszesz plik, a następnie zmienisz sygnaturę czasową, należy wstrzymać powiadomienia o zmianie pliku, ponieważ operacje ponownego zapisu i timestample każda z nich liczą jako oddzielne zdarzenie zmiany pliku. Aby włączyć powiadomienie o zmianie pliku globalnego, należy zamiast tego wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> metodę.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono sposób pomijania powiadomienia o zmianie pliku.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli sprawa obejmuje wiele zmian w pliku, tak jak w przypadku SCC, ważne jest, aby wznowić globalne powiadomienia o zmianie pliku przed wysłaniem alertu do danych dokumentu w celu wznowienia monitorowania zmian plików.
