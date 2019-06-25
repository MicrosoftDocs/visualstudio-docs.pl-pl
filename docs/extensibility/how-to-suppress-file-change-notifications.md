---
title: 'Instrukcje: Pomiń powiadomienia o zmianie pliku | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d7acfb4a5a680aa4be6e93187560cd66b68fa3b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324924"
---
# <a name="how-to-suppress-file-change-notifications"></a>Instrukcje: Pomiń powiadomienia o zmianie pliku
Po zmianie pliku fizycznego reprezentujący buforu tekstowego, okno dialogowe wyświetla komunikat o **czy chcesz zapisać zmiany w następujących elementach?** Jest to nazywane powiadomienie o zmianie pliku. Jeśli wiele zmian mają zostać do pliku, jednak to okno dialogowe wyświetlania wielokrotnie może szybko stać się irytujące.

 Programowe można pominąć to okno dialogowe, korzystając z następującej procedury. Przez pominięcie okna dialogowego, możesz ponownie załadować plik bezpośrednio bez konieczności monit o zapisanie zmian każdorazowo.

## <a name="to-suppress-file-change-notification"></a>Aby wyłączyć powiadomienia o zmianie pliku

1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodę pozwala ustalić obiektu buforu tekstu, który jest skojarzony z otwartego pliku.

2. Bezpośrednie <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiekt, który jest w pamięci, aby zignorować monitorowanie zmian w plikach, uzyskując <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interfejs z <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu (dane dokumentu), a następnie wdrażanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metody z `fIgnore` parametru Ustaw `true`.

3. Wywoływanie metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsów można zaktualizować w pamięci <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu ze zmianami plików (na przykład po dodaniu pola do składnika).

4. Zaktualizuj plik na dysku wprowadzając zmiany, bez uwzględniania wszelkie oczekujące zmiany, które użytkownik może być w toku.

     W ten sposób możesz przekazać <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> powiadomienia o zmianie obiektu w celu wznowienia monitorowania dla pliku, bufor tekstowy w pamięci odzwierciedla wprowadzone został wygenerowany. Bufor tekstowy w pamięci również odzwierciedla wszystkie zmiany oczekujące. Plik na dysku odzwierciedla najnowszy kod wygenerowany przez użytkownika, a wszystkie zapisane wcześniej zmiany przez użytkownika w kodzie edytować użytkownika.

5. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodę, aby powiadomić <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu w celu wznowienia monitorowania pliku powiadomienia o zmianach, ustawiając `fIgnore` parametr `false`.

6. Jeśli planujesz wprowadzić wiele zmian do pliku, tak jak w przypadku kontroli kodu źródłowego (SCC), musisz poinformować usługę zmiany plików globalnej tymczasowo wstrzymać powiadomienia o zmianie pliku.

     Na przykład jeśli ponownego zapisywania pliku, a następnie Zmień sygnaturę czasową, musi zawieszenie powiadomienia o zmianie pliku, ponieważ operacje każdego ponownego zapisywania i sygnaturę czasową liczone jako zdarzenia zmiany w oddzielnym pliku. Aby włączyć powiadomienia o zmianie pliku globalnego, należy zamiast tego wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> metody.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak wyłączyć powiadomienia o zmianie pliku.

```cpp
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

## <a name="robust-programming"></a>Skuteczne programowanie
 Jeżeli obudowę pociąga za sobą wiele zmian do pliku, tak jak w przypadku SCC, następnie jest ważne, aby wznowić powiadomienia o zmianie pliku globalnego przed zgłoszeniem dane dokumentu, aby wznowić monitorowanie zmian w plikach.