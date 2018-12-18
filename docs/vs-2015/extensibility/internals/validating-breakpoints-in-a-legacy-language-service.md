---
title: Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0868e516720fd32a445f60f05f345936d24d6d7a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734978"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Punkt przerwania wskazuje, że wykonywanie programu powinna zostać przerwana w określonym punkcie, gdy są one uruchamiane w debugerze. Użytkownika można umieścić punkt przerwania w dowolnym wierszu w pliku źródłowym, ponieważ edytor ma nie wie, co stanowi prawidłowej lokalizacji punktu przerwania. Gdy debuger jest uruchamiany, wszystkie oznaczone punkty przerwania (nazywane oczekujących punktów przerwania) są powiązane z odpowiedniej lokalizacji w uruchomionego programu. W tym samym czasie, które punkty przerwania są sprawdzane w celu zapewnienia, że ich oznaczenie lokalizacje prawidłowy kod. Na przykład punkt przerwania w komentarz nie jest prawidłowy, ponieważ nie ma kodu w tej lokalizacji w kodzie źródłowym. Debuger wyłącza nieprawidłowy punktów przerwania.  
  
 Ponieważ usługa językowa wie o kodzie źródłowym, są wyświetlane, można sprawdzić punkty przerwania, zanim debuger jest uruchamiany. Można zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodę, aby zwrócić zakresu, określając prawidłową lokalizacją punktu przerwania. Nadal jest weryfikowana lokalizacji punktu przerwania, gdy debuger jest uruchamiany, ale użytkownik jest powiadamiany nieprawidłowy punktów przerwania, bez konieczności oczekiwania na debugera do załadowania.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementowanie obsługi sprawdzania poprawności punktów przerwania  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Metoda otrzymuje położenie punktu przerwania. Implementacji należy zdecydować, czy lokalizacja jest prawidłowa i wskazują, że to zwracając obszaru tekstu, który identyfikuje kod skojarzone z pozycji wiersz punktu przerwania.  
  
-   Zwróć <xref:Microsoft.VisualStudio.VSConstants.S_OK> Jeśli lokalizacja jest prawidłowa, lub <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> Jeśli nie jest prawidłowy.  
  
-   Jeśli punkt przerwania jest prawidłowy zakres tekstu jest wyróżniona wraz z punktu przerwania.  
  
-   Jeśli punkt przerwania jest nieprawidłowa, na pasku stanu pojawi się komunikat o błędzie.  
  
### <a name="example"></a>Przykład  
 Ten przykład pokazuje implementację <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodę, która wywołuje analizator uzyskać zakres kodu (jeśli istnieją) w określonej lokalizacji.  
  
 W tym przykładzie założono, że dodano `GetCodeSpan` metody <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasę weryfikującą zakres tekstu i zwraca `true` przypadku lokalizacji nieprawidłowy punkt przerwania.  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)

