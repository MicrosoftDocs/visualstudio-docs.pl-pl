---
title: 'Przewodnik: Pobieranie listy zainstalowane fragmenty kodu (starsza wersja implementacji) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef16552fbbb051a24d7b2e1fbe5b5266774ef13f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773319"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Przewodnik: Pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fragment kodu jest fragmentem kodu, które mogą być wstawiane do bufor źródłowy za pomocą polecenia menu (umożliwiającą wybierania listy zainstalowanych fragmentów kodu) lub przez wybranie skrótów fragmentu kodu z poziomu listy uzupełniania IntelliSense.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Metoda pobiera wszystkie fragmenty kodu dla określonego języka identyfikator GUID. Skróty klawiaturowe te fragmenty kodu mogą być wstawiane do listy uzupełniania IntelliSense.  
  
 Zobacz [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) szczegółowe informacje na temat Implementowanie fragmentów kodu w usługi językowej pakietu zarządzanego framework (MPF).  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Aby pobrać listę fragmentów kodu  
  
1.  Poniższy kod przedstawia sposób uzyskiwania listy fragmentów kodu dla danego języka. Wyniki są przechowywane w tablicy <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> struktury. Ta metoda jest używana statyczna <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodę, aby uzyskać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> interfejs z <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> usługi. Jednak również użyć dostawcy usług danego pakietu VSPackage i wywołania <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> metody.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>Aby wywołać metodę GetSnippets  
  
1.  Poniższa metoda przedstawiono sposób wywoływania `GetSnippets` metoda po zakończeniu operacji analizowania. <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> Metoda jest wywoływana po operacji analizowania, która została uruchomiona z powodu <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
>  `expansionsList` Tablicy listis ze względu na wydajność w pamięci podręcznej. Zmiany fragmenty kodu nie są odzwierciedlane na liście, dopóki usługa języka jest zatrzymana i ponownie załadować (np. przez zatrzymanie i ponowne uruchomienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]).  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Aby użyć informacji fragmentu kodu  
  
1.  Poniższy kod przedstawia sposób użycia informacji fragment zwracanych przez `GetSnippets` metody. `AddSnippets` Metoda jest wywoływana z analizatora w odpowiedzi na jakiegokolwiek powodu analizy, który jest używany do wypełniania listy fragmentów kodu. To powinno nastąpić po pełnej analizy zostało wykonane po raz pierwszy.  
  
     `AddDeclaration` Metoda tworzy listę deklaracje, które są później jest wyświetlana na liście uzupełniania.  
  
     `TestDeclaration` Klasa zawiera wszystkie informacje, które mogą być wyświetlane na liście uzupełniania, a także typ deklaracji.  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
