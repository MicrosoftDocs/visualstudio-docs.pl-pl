---
title: 'Jak: Zarejestruj bibliotekę w Menedżerze obiektów | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bd1032d2ba67a0c0f3338560a80038ed3215531
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707942"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Jak: Zarejestruj bibliotekę w menedżerze obiektów
Narzędzia do przeglądania symboli, takie jak **Widok klasy,** **Przeglądarka obiektów,** **Przeglądarka połączeń** i **Znajdź wyniki symboli,** umożliwiają wyświetlanie symboli w projekcie lub w komponentach zewnętrznych. Symbole obejmują przestrzenie nazw, klasy, interfejsy, metody i inne elementy języka. Biblioteki śledzą te symbole i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępniają je menedżerowi obiektów, który wypełnia narzędzia danymi.

 Menedżer obiektów śledzi wszystkie dostępne biblioteki. Każda biblioteka musi zarejestrować się w menedżerze obiektów przed podawania symboli dla narzędzi do przeglądania symboli.

 Zazwyczaj można zarejestrować bibliotekę podczas ładowania VSPackage. Jednak w razie potrzeby można to zrobić w innym czasie. Wyrejestrowanie biblioteki po zamknięciu vspackage.

 Aby zarejestrować bibliotekę, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> tej metody. W przypadku biblioteki kodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> zarządzanego użyj tej metody.

 Aby wyrejestrować <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> bibliotekę, użyj tej metody.

 Aby uzyskać odwołanie do menedżera <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>obiektów, <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> przekaż identyfikator `GetService` usługi do metody.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Rejestrowanie i wyrejestrowynie biblioteki za pomocą menedżera obiektów

### <a name="to-register-a-library-with-the-object-manager"></a>Aby zarejestrować bibliotekę w menedżerze obiektów

1. Tworzenie biblioteki.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. Uzyskaj odwołanie do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> typu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> wywołaj metodę.

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>Aby wyrejestrować bibliotekę z menedżerem obiektów

1. Uzyskaj odwołanie do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> typu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> wywołaj metodę.

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność usługi języka starszego](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Jak: Uwidacznianie list symboli dostarczonych przez bibliotekę do menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
