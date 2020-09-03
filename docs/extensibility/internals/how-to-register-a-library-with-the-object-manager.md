---
title: 'Instrukcje: rejestrowanie biblioteki przy użyciu Menedżera obiektów | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 7179bd87fdfd9a2c3fc36958a9d964ec4f790dbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905227"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Instrukcje: rejestrowanie biblioteki przy użyciu Menedżera obiektów
Symbole — narzędzia do przeglądania, takie jak **Widok klasy**, **Przeglądarka obiektów**, **przeglądarka wywołań** i **Znajdź wyniki symboli**, umożliwiają wyświetlanie symboli w projekcie lub w składnikach zewnętrznych. Symbole obejmują obszary nazw, klasy, interfejsy, metody i inne elementy języka. Biblioteki śledzą te symbole i uwidaczniają je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menedżerowi obiektów, który wypełnia narzędzia danymi.

 Menedżer obiektów śledzi wszystkie dostępne biblioteki. Każda biblioteka musi być zarejestrowana w Menedżerze obiektów przed udostępnieniem symboli dla narzędzi do przeglądania symboli.

 Zazwyczaj rejestruje się bibliotekę podczas ładowania pakietu VSPackage. Można je jednak wykonać w innym czasie, zgodnie z wymaganiami. Należy wyrejestrować bibliotekę po zamknięciu pakietu VSPackage.

 Aby zarejestrować bibliotekę, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> metody. W przypadku zarządzanej biblioteki kodu Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody.

 Aby wyrejestrować bibliotekę, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metody.

 Aby uzyskać odwołanie do Menedżera obiektów, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> Przekaż <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Identyfikator usługi do `GetService` metody.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Rejestrowanie i Wyrejestrowywanie biblioteki przy użyciu Menedżera obiektów

### <a name="to-register-a-library-with-the-object-manager"></a>Aby zarejestrować bibliotekę przy użyciu Menedżera obiektów

1. Utwórz bibliotekę.

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

2. Uzyskaj odwołanie do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> typu i Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodę.

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>Aby wyrejestrować bibliotekę przy użyciu Menedżera obiektów

1. Uzyskaj odwołanie do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> typu i Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metodę.

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
- [Rozszerzalność starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Instrukcje: Uwidacznianie list symboli dostarczonych przez bibliotekę do Menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
