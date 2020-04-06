---
title: Uzyskiwanie listy zainstalowanych fragmentów kodu (Starsza wersja) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d5ef857973555c4b2d201f98957bd2c39328b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703654"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Przewodnik: pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)
Fragment kodu to fragment kodu, który można wstawić do buforu źródłowego za pomocą polecenia menu (które umożliwia wybór spośród listy zainstalowanych fragmentów kodu) lub wybierając skrót fragmentu kodu z listy uzupełniania IntelliSense.

 Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> pobiera wszystkie fragmenty kodu dla określonego identyfikatora GUID języka. Skróty dla tych fragmentów można wstawić do listy uzupełnień IntelliSense.

 Zobacz [obsługa fragmentów kodu w usłudze języka starszego, aby](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) uzyskać szczegółowe informacje na temat implementowania fragmentów kodu w usłudze języka managed package framework (MPF).

### <a name="to-retrieve-a-list-of-code-snippets"></a>Aby pobrać listę fragmentów kodu

1. Poniższy kod pokazuje, jak uzyskać listę fragmentów kodu dla danego języka. Wyniki są przechowywane w <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> tablicy struktur. Ta metoda używa metody <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> statycznej, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> aby <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> uzyskać interfejs z usługi. Jednak można również użyć dostawcy usług podane do VSPackage i wywołać <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> metodę.

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

### <a name="to-call-the-getsnippets-method"></a>Aby wywołać Metodę GetSnippets

1. Poniższa metoda pokazuje, `GetSnippets` jak wywołać metodę po zakończeniu operacji analizy. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> jest wywoływana po operacji analizy, która <xref:Microsoft.VisualStudio.Package.ParseReason>została uruchomiona z powodu .

> [!NOTE]
> Lista `expansionsList` tablic jest buforowana ze względu na wydajność. Zmiany fragmentów kodu nie są odzwierciedlane na liście, dopóki usługa językowa nie zostanie zatrzymana [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]i ponownie załadowana (na przykład przez zatrzymanie i ponowne uruchomienie).

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

### <a name="to-use-the-snippet-information"></a>Aby użyć informacji o urywek

1. Poniższy kod pokazuje, jak używać informacji urywek zwracanych przez `GetSnippets` metodę. Metoda `AddSnippets` jest wywoływana z analizatora w odpowiedzi na wszelkie przyczyny analizy, która jest używana do wypełniania listy fragmentów kodu. Powinno to nastąpić po zakończeniu pełnej analizy po raz pierwszy.

     Metoda `AddDeclaration` tworzy listę deklaracji, które są później wyświetlane na liście zakończenia.

     Klasa `TestDeclaration` zawiera wszystkie informacje, które mogą być wyświetlane na liście zakończenia, a także typ deklaracji.

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
- [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
