---
title: Ponowne formatowanie kodu w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eb0dac5e1282d544df9c04bf4c12303fb391739d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436647"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Ponowne formatowanie kodu w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kod źródłowy może ponownie sformatowane, przez normalizowanie stosowania wcięć i białe znaki. Może to obejmować wstawiania lub usuwając spacje lub tabulatory na początku każdego wiersza, dodawanie nowych wierszy między liniami lub zastępowania miejsca do magazynowania za pomocą karty lub kart przy użyciu miejsc do magazynowania.  
  
> [!NOTE]
> **Uwaga** Wstawianie i usuwanie znaków nowego wiersza może mieć wpływ na znaczników, takich jak punkty przerwania i zakładki, ale dodając lub usuwając spacje lub tabulatory nie ma wpływu na znaczników.  
  
 Użytkownicy mogą uruchamiać operację reformatting, wybierając **Formatuj zaznaczenie** lub **Formatuj dokument** z **zaawansowane** menu **Edytuj**menu. Operacja reformatting mogą być też wywoływane po wstawieniu fragmentu kodu lub określonego znaku. Na przykład po wpisaniu zamykającego nawiasu klamrowego w języku C# wszystko pomiędzy otwierający nawias klamrowy dopasowania i zamknij nawiasów klamrowych jest automatycznie z wcięciami, aby zapewnić odpowiedni poziom.  
  
 Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wysyła **Formatuj zaznaczenie** lub **Formatuj dokument** polecenia do usługi języka <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy wywołania <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.Source> klasy. Do obsługi formatowania, konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metody i dostarczyć własne formatowanie kodu.  
  
## <a name="enabling-support-for-reformatting"></a>Włączanie obsługi formatowania  
 Do obsługi formatowania, `EnableFormatSelection` parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> musi być równa `true` po dokonaniu rejestracji Twojego pakietu VSPackage. To ustawienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> właściwość `true`. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Metoda zwraca wartość tej właściwości. Jeśli zostanie zwrócona wartość true, <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy wywołania <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Implementowanie ponownego formatowania  
 Aby zaimplementować formatowania, należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.Source> klasy, a także Przesłoń <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metody. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Obiekt w tym artykule opisano zakres do formatowania i <xref:Microsoft.VisualStudio.Package.EditArray> obiekt zawiera zmiany wprowadzone na zakres. Należy pamiętać, że ten zakres można całego dokumentu. Jednak ponieważ może być wiele zmian w zakresie, wszystkie zmiany powinny być odwracalnego w ramach jednej akcji. Aby to zrobić, opakować wszystkie zmiany w <xref:Microsoft.VisualStudio.Package.CompoundAction> obiektu (patrz sekcja "Używanie klasy CompoundAction" w tym temacie).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład gwarantuje, że istnieje pojedyncza spacja po każdym przecinku w zaznaczeniu, chyba że przecinek następuje karty lub znajduje się na końcu wiersza. Końcowe spacje, po usunięciu ostatniego przecinkami w wierszu. Zobacz sekcję "Przy użyciu klasy CompoundAction" w tym temacie, aby zobaczyć, jak ta metoda jest wywoływana z <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metody.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>Używanie klasy CompoundAction  
 Wszystkie ponownego formatowania na sekcję kodu powinny być odwracalnego w ramach jednej akcji. Można to zrobić za pomocą <xref:Microsoft.VisualStudio.Package.CompoundAction> klasy. Ta klasa opakowuje zestaw operacji edycji w buforze tekstu operacji edycji jednego.  
  
### <a name="example"></a>Przykład  
 Oto przykład sposobu użycia <xref:Microsoft.VisualStudio.Package.CompoundAction> klasy. Zobacz przykład w sekcji "Wdrażanie pomocy technicznej dla formatowania" w tym temacie przedstawiono przykład `DoFormatting` metody.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
