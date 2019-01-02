---
title: 'Instrukcje: Rejestrowanie biblioteki przy użyciu Menedżera obiektów | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ed3913b8031283b20589a670c5d2da6e51a8dec
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941982"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Instrukcje: Rejestrowanie biblioteki przy użyciu Menedżera obiektów
Symbole, przeglądania narzędzia, takie jak **Widok klas**, **przeglądarki obiektów**, **przeglądarce wywołań** i **wyniki wyszukiwania symboli**, można wyświetlać symbole w projekcie lub w składnikach zewnętrznych. Symbole obejmują przestrzenie nazw, klasy, interfejsy, metod i inne elementy języka. Biblioteki śledzenie tych symboli i udostępnić je do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menedżera obiektów, która wypełnia narzędzia z danymi.  
  
 Menedżer obiektów przechowuje informacje o wszystkich dostępnych bibliotek. Każdej biblioteki należy zarejestrować przy użyciu Menedżera obiektów przed symbole dla narzędzi do przeglądania symboli.  
  
 Zazwyczaj należy zarejestrować bibliotekę, podczas ładowania pakietu VSPackage. Jednak go może odbywać się w innym czasie zgodnie z potrzebami. Podczas wyłączania pakietu VSPackage wyrejestrowano biblioteki.  
  
 Aby zarejestrować bibliotekę, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> metody. Biblioteki kodu zarządzanego, można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody.  
  
 Aby wyrejestrować bibliotekę, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metody.  
  
 Aby uzyskać odwołanie do Menedżera obiektów <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, przekazać <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> identyfikator do usługi `GetService` metody.  
  
## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Rejestrowanie i wyrejestrowywanie bibliotekę z Menedżera obiektów  
  
### <a name="to-register-a-library-with-the-object-manager"></a>Aby zarejestrować bibliotekę z Menedżera obiektów  
  
1.  Utwórz bibliotekę.  
  
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
  
2.  Uzyskaj odwołanie do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> wpisz i wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody.  
  
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
  
### <a name="to-unregister-a-library-with-the-object-manager"></a>Aby wyrejestrować bibliotekę z Menedżera obiektów  
  
1.  Uzyskaj odwołanie do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> wpisz i wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metody.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzalność usługi starszego języka](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Instrukcje: Uwidacznianie listy symboli udostępnianych przez bibliotekę dla Menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)