---
title: Sprawdzanie poprawności punktów przerwania w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704097"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej
Punkt przerwania wskazuje, że wykonanie programu należy zatrzymać w określonym punkcie, gdy jest uruchamiany w debugerze. Użytkownik może umieścić punkt przerwania w dowolnym wierszu w pliku źródłowym, ponieważ edytor nie ma wiedzy o tym, co stanowi prawidłową lokalizację dla punktu przerwania. Po uruchomieniu debugera wszystkie oznaczone punkty przerwania (nazywane oczekującymi punktami przerwania) są powiązane z odpowiednią lokalizacją w uruchomionym programie. W tym samym czasie punkty przerwania są sprawdzane, aby upewnić się, że oznaczają prawidłowe lokalizacje kodu. Na przykład punkt przerwania na komentarz jest nieprawidłowy, ponieważ nie ma kodu w tej lokalizacji w kodzie źródłowym. Debuger wyłącza nieprawidłowe punkty przerwania.

 Ponieważ usługa języka wie o kod źródłowy są wyświetlane, można sprawdzić poprawność punktów przerwania przed uruchomieniem debugera. Można zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodę zwracania zakresu określającego prawidłową lokalizację dla punktu przerwania. Lokalizacja punktu przerwania jest nadal sprawdzana po uruchomieniu debugera, ale użytkownik jest powiadamiany o nieprawidłowych punktach przerwania bez oczekiwania na załadowanie debugera.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementowanie pomocy technicznej dla sprawdzania poprawności punktów przerwania

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> jest podana położenie punktu przerwania. Implementacja musi zdecydować, czy lokalizacja jest prawidłowa, i wskazać to, zwracając zakres tekstu, który identyfikuje kod skojarzony z położeniem wiersza punktu przerwania.

- Wróć, <xref:Microsoft.VisualStudio.VSConstants.S_OK> jeśli lokalizacja jest <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> prawidłowa lub jeśli jest nieprawidłowa.

- Jeśli punkt przerwania jest prawidłowy, zakres tekstu jest wyróżniony wraz z punktem przerwania.

- Jeśli punkt przerwania jest nieprawidłowy, na pasku stanu pojawi się komunikat o błędzie.

### <a name="example"></a>Przykład
 W tym przykładzie <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> pokazano implementację metody, która wywołuje analizatora, aby uzyskać zakres kodu (jeśli istnieje) w określonej lokalizacji.

 W tym przykładzie przyjęto `GetCodeSpan` założenie, <xref:Microsoft.VisualStudio.Package.AuthoringSink> że dodano metodę do `true` klasy, która sprawdza poprawność zakresu tekstu i zwraca, jeśli jest prawidłową lokalizacją punktu przerwania.

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
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
